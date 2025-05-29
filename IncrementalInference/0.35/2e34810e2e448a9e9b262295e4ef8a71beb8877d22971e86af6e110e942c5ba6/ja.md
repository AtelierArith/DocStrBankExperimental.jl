```julia
deconvSolveKey(dfg, refSym, refKey, tstSym, tstKey; tfg)

```

2つの変数間およびsolveKeys間の相対差を計算します。

例

```julia
fg = generateGraph_Kaess()
solveTree!(fg, storeOld=true)
# 初期状態から解決までのソルバーによって引き起こされる相対運動を計算します。
pts = deconvSolveKey(fg, :x1, :default, :x1, :graphinit)
```

ノート

  * より良いインプレース操作のためにユーザー `tfg::AbstractDFG` を渡すことができます。

開発ノート

  * TODO 内部で新しいtfgを構築するのではなく、dfgを使用します。

関連

[`approxDeconv`](@ref), [`mmd`](@ref)
