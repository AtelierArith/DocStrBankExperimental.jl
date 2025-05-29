```julia
resetInitialValues!(dest; ...)
resetInitialValues!(dest, src; ...)
resetInitialValues!(dest, src, initKey; ...)
resetInitialValues!(dest, src, initKey, solveKey; varList)

```

`initKey::Symbol=:graphinit` の値に従って `dest::AbstractDFG` の solveKey 値を設定します。

ノート

  * 2つの DFG と異なるキー値を使用するための柔軟性があります。詳細は例とコードを参照してください。
  * `varList::Vector{Symbol}` で特定することもできます。
  * `dest` グラフを返します。
  * supersolve メカニズムを使用します。

例

```julia
resetInitialValues!(fg)
resetInitialValues!(fg1,fg2)  # 2 から 1 へ
resetInitialValues!(fg1,fg1,:myotherinit)  # solveKey :default に異なる初期値を使用
resetInitialValues!(fg1,fg1,:graphinit, :mysolver) # solveKey=:default ではなく :mysolver に
resetInitialValues!(fg1, varList=[:x1;:l3])  # 特定の変数のみ

# `fgNew` オブジェクトに、`fg` を変更せずに
fgNew = deepcopy(fg)
resetInitialValues!(fgNew,fg)
```

関連

initVariable!, graphinit (キーワード)
