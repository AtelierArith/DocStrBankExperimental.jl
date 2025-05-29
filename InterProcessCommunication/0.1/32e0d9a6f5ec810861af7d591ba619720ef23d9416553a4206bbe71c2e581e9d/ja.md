```julia
TimeVal(sec, usec)
```

は、エポックからの整数秒数 `sec` と整数マイクロ秒数 `usec` に対して `TimeVal` のインスタンスを生成します。

```julia
TimeVal(sec)
```

は、エポックからの、場合によっては小数の秒数 `sec` を持つ `TimeVal` のインスタンスを生成します。引数は [`TimeSpec`](@ref) のインスタンスでも構いません。

`now(TimeVal)` を呼び出すことで、`TimeVal` のインスタンスとして現在の時刻を取得できます。

`TimeVal` のインスタンスを含む加算および減算は `TimeVal` の結果を生成します。例えば：

```julia
now(TimeVal) + 3.4
```

は、現在の時刻に `3.4` 秒を加えた `TimeVal` のインスタンスを生成します。

```julia
typemin(TimeVal)
typemax(TimeVal)
```

は、それぞれ `TimeVal` のインスタンスに対する最小および最大の正規化された時間値を返します。
