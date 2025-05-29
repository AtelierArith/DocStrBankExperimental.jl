```
fit(gbm::GBM, X::AbstractArray; delta=1e-1 [, opts])
```

GBMの重みパラメータをデータ`X`にフィットさせます。

# 引数

  * `delta::Float`: パラメータを間引くための閾値。

`opts`辞書で提供できるオプション:

  * `:alpha` - L1正則化項の減衰率。(デフォルト: 0.01)
  * `:beta` - 逆温度。(デフォルト: 1.0)
  * `:lr` - 学習率。(デフォルト: 1.0)
  * `:epochs` - SGDで許可される最大ステップ数。(デフォルト: 20)
  * `:n_iter` - 学習の繰り返し回数。(デフォルト: 100)

# 参考文献

  * E. Aurell & M. Ekeberg, Phys. Rev. Lett. **108**, 090201 (2012).

# 例

```jldoctest
julia> using InverseIsing

julia> samples = [1 -1 -1;] # スピン配置。

julia> model = GBM(3) # ユニット数を設定。

julia> fit(model, samples)

julia> W = infer(model); output = decode(W)

julia> output
OrderedCollections.OrderedDict{Tuple{Int64,Int64},Int64} with 3 entries:
  (1, 2) => -1
  (1, 3) => -1
  (2, 3) => 1
```

```
上記の例は、(1, 2)と(1, 3)の間の相互作用が反強磁性結合であり、(2, 3)のみが強磁性結合であることを意味します。
```
