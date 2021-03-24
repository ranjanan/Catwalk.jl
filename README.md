# Catwalk.jl

![Lifecycle](https://img.shields.io/badge/lifecycle-maturing-blue.svg)<!--
![Lifecycle](https://img.shields.io/badge/lifecycle-experimental-orange.svg)
![Lifecycle](https://img.shields.io/badge/lifecycle-stable-green.svg)
![Lifecycle](https://img.shields.io/badge/lifecycle-retired-orange.svg)
![Lifecycle](https://img.shields.io/badge/lifecycle-archived-red.svg)
![Lifecycle](https://img.shields.io/badge/lifecycle-dormant-blue.svg) -->
[![Documentation](https://img.shields.io/badge/docs-dev-blue.svg)](https://tisztamo.github.io/Catwalk.jl/dev/)
[![CI](https://github.com/tisztamo/Catwalk.jl/actions/workflows/ci.yml/badge.svg)](https://github.com/tisztamo/Catwalk.jl/actions/workflows/ci.yml)

Catwalk.jl can speed up long-running Julia processes by minimizing the
overhead of dynamic dispatch. It is a JIT compiler that continuosly
re-optimizes dispatch code based on data collected at runtime.

![Speedup demo](docs/src/assets/catwalk-speeddemo.gif)
[source code of this test](https://github.com/tisztamo/Catwalk.jl/blob/main/test/scheduling.jl)

It profiles user-specified call sites, estimating the distribution of
dynamically dispatched types during runtime, and generates fast
static routes for the most frequent ones on the fly.

The statistical profiler has very low overhead and can be configured
to handle situations where the distribution of dispatched types
changes relatively fast.

To minimize compilation overhead, recompilation only occurs when the
distribution changed enough so that the  included cost model predicts
significant speedup compared to the best version that was previously
compiled.

[Documentation (dev)]((https://tisztamo.github.io/Catwalk.jl/dev/))