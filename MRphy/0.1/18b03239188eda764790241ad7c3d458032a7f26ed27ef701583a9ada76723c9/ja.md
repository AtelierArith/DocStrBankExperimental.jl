```
freePrec!(M, t; Δf=0u"Hz", T1=(Inf)u"s", T2=(Inf)u"s")
```

スピン、`M`、は時間 `t` によって自由前処理を行います。`M` は結果によって更新されます。

*入力*:

  * `M::TypeND(Real, [2])` (nM, xyz): 入力スピンの磁化。
  * `t::T0D` (1,): 自由前処理の期間。

*キーワード*:

  * `T1 & T2 ::TypeND(T0D, [0,1])`: グローバル、(1,); スピンごと、(nM,1)。

*出力*:

  * `M::TypeND(Real, [2])` (nM, xyz): 出力スピンの磁化。

参照: [`freePrec`](@ref)。
