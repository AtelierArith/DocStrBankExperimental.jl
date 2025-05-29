```
apply_coupling!(system, coupling, simulator, neighbors=nothing, step_n=0;
                n_threads=Threads.nthreads(), rng=Random.default_rng())
```

シミュレーションを変更するためにカプラーを適用します。

カプラーが現在保存されている力を無効にしたかどうかを返します。たとえば、座標を変更することによってです。この情報は一部のシミュレーターにとって有用です。`coupling`がタプルまたは名前付きタプルである場合、各カプラーは順番に適用されます。カスタムカプラーはこの関数を実装する必要があります。
