```
timestamp(deps::Union{PyObject, <:Real, Missing}=missing)
```

これらの関数は通常、プロファイリングのために[`bind`](@ref)と一緒に使用されます。マルチスレッド環境では、タイミングが非常に正確ではないことに注意してください。

  * `deps`: `deps`は、タイムスタンプを返す前に常に実行されます。

# 例

```julia
a = constant(3.0)
t0 = timestamp(a)
sleep_time = sleep_for(a)
t1 = timestamp(sleep_time)
sess = Session(); init(sess)
t0_, t1_ = run(sess, [t0, t1])
time = t1_ - t0_
```
