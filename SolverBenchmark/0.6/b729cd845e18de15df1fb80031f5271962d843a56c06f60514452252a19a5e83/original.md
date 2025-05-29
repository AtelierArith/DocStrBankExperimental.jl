```
stats = judgement_results_to_dataframes(judgement)
```

Convert `BenchmarkJudgement` results to a dictionary of `DataFrame`s.

Inputs:

  * `judgement::BenchmarkJudgement`: the result of, e.g.,

    ```
    commit = benchmarkpkg(mypkg)  # benchmark a commit or pull request
    main = benchmarkpkg(mypkg, "main")  # baseline benchmark
    judgement = judge(commit, main)
    ```

Output:

  * `stats::Dict{Symbol,Dict{Symbol,DataFrame}}`: a dictionary of   `Dict{Symbol,DataFrame}`s containing the target and baseline benchmark results.   The elements of this dictionary are the same as those returned by   `bmark_results_to_dataframes(main)` and `bmark_results_to_dataframes(commit)`.
