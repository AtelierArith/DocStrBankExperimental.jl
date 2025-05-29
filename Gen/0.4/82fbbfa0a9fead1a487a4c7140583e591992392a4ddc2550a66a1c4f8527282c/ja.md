```
HeterogeneousMixture(distributions::Vector{Distribution{T}}) where {T}
```

与えられた基本分布のリストの混合物である新しい分布を定義します。

引数は、各混合成分のための基本分布のベクトルです。

基本分布は同じ出力タイプでなければならないことに注意してください。

例：

```julia
uniform_beta_mixture = HeterogeneousMixture([uniform, beta])
```

結果として得られる混合分布は `n+1` の引数を取ります。ここで `n` はリスト内の各分布が取る引数の合計です。混合分布への最初の引数は、非負の混合重みのベクトルで、合計は 1.0 でなければなりません。残りの引数は、コンストラクタに渡された順序で各混合成分分布への引数です。

例：

```julia
@gen function foo()
    # [`lower`, `upper`] の区間での一様分布の混合物
    # および alpha パラメータ `a` と beta パラメータ `b` を持つベータ分布
    # 一様分布の重みは 0.4 で、ベータ分布の重みは 0.6
    x ~ uniform_beta_mixture([0.4, 0.6], lower, upper, a, b)
end
```
