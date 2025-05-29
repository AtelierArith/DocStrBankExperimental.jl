```
run!(
    model::Physics{T,F,M,Tu,E,D,BI}; 
    output=VTK(), pref=nothing, ncorrectors=0, inner_loops=0
    ) where{T<:Transient,F<:WeaklyCompressible,M,Tu,E,D,BI} = 
begin
    residuals = cpiso!(model, config)
    return residuals
end
```

弱圧縮流体のためのPISOアルゴリズムを使用して、圧縮性過渡ソルバーを呼び出します。

# 入力

  * `model` はユーザーによって定義された `Physics` モデルを表します。
  * `config` ユーザーによって定義された構成構造体で、ソルバー、スキーム、ランタイム、およびハードウェア構造の構成詳細を含みます。
  * `output` シミュレーション結果に使用される形式を `VTK()` または `OpenFOAM()` から選択します（デフォルト = `VTK()`）
  * `pref` 圧力を定義するBCがない場合の基準圧力値。非圧縮性ソルバーのみ。

# 出力

この関数は、残差にアクセスするための `NamedTuple` を返します（例: `residuals.Ux`）で、以下のエントリがあります：

  * `Ux`  - 各反復のx-速度残差のベクトル。
  * `Uy`  - 各反復のy-速度残差のベクトル。
  * `Uz`  - 各反復のy-速度残差のベクトル。
  * `p`   - 各反復の圧力残差のベクトル。
  * `e`   - 各反復のエネルギー残差のベクトル。
