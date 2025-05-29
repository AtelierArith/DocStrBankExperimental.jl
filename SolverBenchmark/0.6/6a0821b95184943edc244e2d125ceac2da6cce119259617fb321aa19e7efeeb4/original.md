```
p = profile_package(judgement)
```

Produce performance profiles based on `PkgBenchmark.BenchmarkJudgement` results.

Inputs:

  * `judgement::BenchmarkJudgement`: the result of, e.g.,

    ```
    commit = benchmarkpkg(mypkg)  # benchmark a commit or pull request
    main = benchmarkpkg(mypkg, "main")  # baseline benchmark
    judgement = judge(commit, main)
    ```
