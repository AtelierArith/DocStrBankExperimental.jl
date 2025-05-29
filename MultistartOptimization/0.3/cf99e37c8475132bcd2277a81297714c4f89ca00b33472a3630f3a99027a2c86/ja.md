```julia
multistart_minimization(
    multistart_method,
    local_method,
    minimization_problem;
    use_threads,
    prepend_points
)

```

`minimization_problem`を`multistart_method`内で`local_method`を使用して解決します。

`use_threads`が指定されている場合、初期点の探索は`Threads.@spawn`を使用して並列化されます。

`prepend_points`には、Sobolシーケンスの前に追加される初期の開始点のベクトルを含める必要があります。これは、最適解の近くに推測がある場合に便利です。
