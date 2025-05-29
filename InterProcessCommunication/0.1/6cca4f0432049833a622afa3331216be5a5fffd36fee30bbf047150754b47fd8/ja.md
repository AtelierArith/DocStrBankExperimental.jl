```julia
TimeSpec(sec, nsec)
```

は、エポックからの整数秒数 `sec` と整数ナノ秒数 `nsec` に対する `TimeSpec` のインスタンスを生成します。

```julia
TimeSpec(sec)
```

は、エポックからの、場合によっては小数の秒数 `sec` に対する `TimeSpec` のインスタンスを生成します。引数は [`TimeVal`](@ref) のインスタンスでも構いません。

`now(TimeSpec)` を呼び出すと、`TimeSpec` のインスタンスとして現在の時刻を取得できます。

`TimeSpec` のインスタンスを含む加算および減算は `TimeSpec` の結果を生成します。例えば：

```julia
now(TimeSpec) + 3.4
```

は、現在の時刻に `3.4` 秒を加えた `TimeSpec` のインスタンスを生成します。

```julia
typemin(TimeSpec)
typemax(TimeSpec)
```

は、それぞれ `TimeSpec` のインスタンスに対する最小および最大の正規化された時間値を返します。
