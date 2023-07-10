# Benchmarks

The benchmarks crate contains currently the following benchmarks:

* [sequential_throughput](benches/throughput_sequential.rs): Runs the Restate runtime and ingest counter.Counter/GetAndAdd requests sequentially (same key)
* [parallel_throughput](benches/throughput_parallel.rs): Runs the Restate runtime and ingest counter.Counter/GetAndAdd requests concurrently (random key)

## Prerequisites

The above-mentioned benchmarks require the [counter.Counter service](https://github.com/restatedev/e2e/blob/a500164a31d58c0ee65ae77a7f99a8a2ef1825cb/services/node-services/src/counter.ts) running on `localhost:8080`.
See the [node services' readme](https://github.com/restatedev/e2e/blob/a500164a31d58c0ee65ae77a7f99a8a2ef1825cb/services/node-services/README.md) for details how to run the services.

## Running the benchmarks

All benchmarks can be run via:

```shell
cargo bench 
```

To run a single benchmark run it via:

```shell
cargo bench --bench throughput_parallel
```

## Profiling the benchmarks

In order to profile the benchmarks select a benchmark and pass the `--profil-time=<time_to_run>` option:

```shell
cargo bench --bench throughput_parallel -- --profile-time=30
```

This will profile the *throughput_parallel* benchmark for *30 s*.
The profiler will generate a flamegraph under `target/criterion/<name_of_benchmark>/profile/flamegraph.svg`.