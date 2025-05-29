```
ReTestItems.runtests()
ReTestItems.runtests(mod::Module)
ReTestItems.runtests(paths::AbstractString...)
```

Execute `@testitem` tests.

Only files ending in `_test.jl` or `_tests.jl` will be searched for test items.

If directory or file paths are passed, only those directories and files are searched. If no arguments are passed, the `src/` and `test/` directories of the current project are searched for `@testitem`s.

# Keywords

## Filtering `@testitem`s

  * `name::Union{Regex,AbstractString,Nothing}=nothing`: Used to filter `@testitem`s by their name. `AbstractString` input will only keep the `@testitem` that exactly matches `name`, `Regex` can be used to partially match multiple `@testitem`s. By default, no filtering is applied.
  * `tags::Union{Symbol,AbstractVector{Symbol},Nothing}=nothing`: Used to filter `@testitem`s by their tags. A single tag can be used to match any `@testitem` that contains it, when multiple tags are provided, only `@testitem`s that contain *all* of the tags will be run. By default, no filtering is applied.

`name` and `tags` filters are applied together and only those `@testitem`s that pass both filters will be run.

## Configuring `runtests`

  * `testitem_timeout::Real`: The number of seconds to wait until a `@testitem` is marked as failed. Defaults to 30 minutes. Can also be set using the `RETESTITEMS_TESTITEM_TIMEOUT` environment variable. If a `@testitem` sets its own `timeout` keyword, then that takes precedence. Fractional values are rounded up to the nearest second. Note timeouts are currently only applied when `nworkers > 0`.
  * `retries::Int=0`: The number of times to retry a `@testitem` if either tests do not pass or, if running with multiple worker processes, the worker fails or hits the timeout limit while running the tests. Can also be set using the `RETESTITEMS_RETRIES` environment variable. If a `@testitem` sets its own `retries` keyword, then the maximum of these two retry numbers will be used as the retry limit for that `@testitem`. When `report=true`, the report will contain information for all runs of a `@testitem` that was retried.
  * `nworkers::Int`: The number of worker processes to use for running `@testitem`s. Default 0. Can also be set using the `RETESTITEMS_NWORKERS` environment variable.
  * `nworker_threads::Union{String,Int}`: The number of threads to use for each worker process. Defaults to 2. Can also be set using the `RETESTITEMS_NWORKER_THREADS` environment variable. Interactive threads are supported through a string (e.g. "auto,2").
  * `worker_init_expr::Expr`: an expression that will be run on each worker process before any tests are run. Can be used to load packages or set up the environment. Must be a `:block` expression.
  * `test_end_expr::Expr`: an expression that will be run after each testitem is run. Can be used to verify that global state is unchanged after running a test. Must be a `:block` expression. The `test_end_expr` is evaluated whether a testitem passes, fails, or errors. If the `testsetup` fails, then the `test_end_expr` is not run.
  * `gc_between_testitems::Bool`: If `true`, a full garbage collection (GC) will be run after each test item is run. Defaults to `nworkers > 1`, i.e. `true` when running with multiple worker processes, since multiple worker processes cannot coordinate to trigger Julia's GC, and it should not be necessary to invoke the GC directly if running without workers or with a single worker (since the GC will be triggered automatically by the single process running all the tests). Can also be set using the `RETESTITEMS_GC_BETWEEN_TESTITEMS` environment variable. Tip: For complete control over GC, set `gc_between_testitems=false` and manually trigger GC in `test_end_expr`.
  * `memory_threshold::Real`: Sets the fraction of memory that can be in use before a worker processes are restarted to free memory. Defaults to 0.99. Only supported with `nworkers > 0`. For example, if set to 0.8, then when >80% of the available memory is in use, a worker process will be killed and replaced with a new worker before the next testitem is run. The testitem will then be run on the new worker process, regardless of if memory pressure dropped below the threshold. If the memory pressure remains above the threshold, then a worker process will again be replaced before the next testitem is run. Can also be set using the `RETESTITEMS_MEMORY_THRESHOLD` environment variable. **Note**: the `memory_threshold` keyword is experimental and may be removed in future versions.
  * `report::Bool=false`: If `true`, write a JUnit-format XML file summarising the test results. Can also be set using the `RETESTITEMS_REPORT` environment variable. The location at which the XML report is saved can be set using the `RETESTITEMS_REPORT_LOCATION` environment variable. By default the report will be written at the root of the project being tested.
  * `logs::Symbol`: Handles how and when we display messages produced during test evaluation. Can be one of:

      * `:eager`: Everything is printed to `stdout` immediately, like in a regular Julia session.
      * `:batched`: Logs are saved to a file and then printed when the test item is finished.
      * `:issues`: Logs are saved to a file and only printed if there were any errors or failures.

    For interative sessions, `:eager` is the default when running with 0 or 1 worker processes, `:batched` otherwise. For non-interactive sessions, `:issues` is used by default.
  * `verbose_results::Bool`: If `true`, the final test report will list each `@testitem`, otherwise the results are aggregated. Default is `false` for non-interactive sessions or when `logs=:issues`, `true` otherwise.
  * `validate_paths::Bool=false`: If `true`, `runtests` will throw an error if any of the `paths` passed to it cannot contain test files, either because the path doesn't exist or the path points to a file which is not a test file. Default is `false`. Can also be set using the `RETESTITEMS_VALIDATE_PATHS` environment variable.
  * `timeout_profile_wait::Real=0`: When non-zero, a worker that times-out will trigger a CPU profile  for which we will wait `timeout_profile_wait` seconds before terminating the worker.  Zero means no profile will be taken. Can also be set using the `RETESTITEMS_TIMEOUT_PROFILE_WAIT`  environment variable. See the [Profile documentation](https://docs.julialang.org/en/v1/stdlib/Profile/#Triggered-During-Execution)  for more information on triggered profiles. Note you can use `worker_init_expr` to tweak the profile settings on workers.
  * `failfast::Bool=false`: If true, no additional testitems are run after a testitem fails. A testitem is considered to have failed if it does not pass after retries. Note that in the current implementation testitems already running on other workers in parallel with the failing testitem are allowed to complete, but this may be improved in a future version. Can also be set using the `RETESTITEMS_FAILFAST` environment variable.
  * `testitem_failfast::Bool=failfast`: If true, a testitem stops as soon as there is a test failure or error. Can also be set using the `RETESTITEMS_TESTITEM_FAILFAST` environment variable. Defaults to the value passed to the `failfast` keyword. If a `@testitem` sets its own `failfast` keyword, then that takes precedence. Note that the `testitem_failfast` keyword only takes effect in Julia v1.9+ and is ignored in earlier Julia versions.
