```
lat_getu(sol, sp, lrs::LatticeReactionSystem; t = nothing)
```

`LatticeReactionSystem`に基づくシミュレーションの解をさまざまな希望する形式で取得するための関数です。一般的に、`LatticeReactionSystem`の`sol`内の値は、ユーザーが直接解釈できない方法で順序付けられています。さらに、これらの解に対する通常のCatalystインターフェース（例：`sol[:X]`）は機能しません。したがって、この関数が代わりに使用されます。

出力はベクトルであり、各位置にはspの値（入力`t`に応じて、時間ステップまたはその時点での値）が含まれています。その形状は格子に依存します（異種初期条件と同様の形式を使用）。すなわち、NxMの直交格子の場合、値はNxMの行列です。マスクされた格子の場合、値は疎行列です。グラフ格子の場合、値はベクトルです（n番目の位置の値はn番目の頂点におけるspの値に対応します）。

引数：

  * `sol`: 取得したい値を持つ解。
  * `sp`: 更新したい種の値。記号形式（例：`X`）またはシンボル（例：`:X`）のいずれかで提供できます。
  * `lrs`: 解を生成するためにシミュレーションされた`LatticeReactionSystem`。
  * `t = nothing`: `nothing`の場合、保存されたすべての時間ステップにわたる解を単純に返します（デフォルト）。代わりに`t`がベクトル（または値の範囲）の場合、これらの時間点で補間された解を返します。

注意事項：

  * `lat_getu`はパフォーマンスの最適化がされていません。ただし、かなりのパフォーマンスを持つはずですが、非常に多くの回数呼び出されると制限があるかもしれません。
  * 長期的には、この関数はより洗練されたインターフェースに置き換えられる可能性があります。

例：

```julia
using Catalyst, OrdinaryDiffEqDefault

# `LatticeReactionSystem`を準備します。
rs = @reaction_network begin
    (k1,k2), X1 <--> X2
end
tr = @transport_reaction D X1
lrs = LatticeReactionSystem(rs, [tr], CartesianGrid((2,2)))

# 問題を作成します。
u0 = [:X1 => 1, :X2 => 2]
tspan = (0.0, 10.0)
ps = [:k1 => 1, :k2 => 2.0, :D => 0.1]

oprob = ODEProblem(lrs1, u0, tspan, ps)
osol = solve(oprob)
lat_getu(osol, :X1, lrs) # 各時間ステップでのX1の値を返します。
lat_getu(osol, :X1, lrs; t = 0.0:10.0) # 時間0.0、1.0、...、10.0でのX1の値を返します。
```
