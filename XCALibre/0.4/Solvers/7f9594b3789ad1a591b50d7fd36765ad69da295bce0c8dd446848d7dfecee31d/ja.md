```
run!(
    model::Physics{T,F,M,Tu,E,D,BI}, config; 
    output=VTK(), pref=nothing, ncorrectors=0, inner_loops=0
    ) where{T<:Transient,F<:Incompressible,M,Tu,E,D,BI} = 
begin
    residuals = piso!(model, config, pref=pref); #, pref=0.0)
    return residuals
end
```

PISOアルゴリズムを使用して非圧縮性過渡ソルバーを呼び出します。

# 入力

  * `model` はユーザーによって定義された `Physics` モデルを表します。
  * `config` ユーザーによって定義された構成構造体で、ソルバー、スキーム、ランタイム、およびハードウェア構造の構成詳細を含みます。
  * `output` シミュレーション結果に使用される形式を `VTK()` または `OpenFOAM()` から選択します（デフォルト = `VTK()`）。
  * `pref` 圧力を定義する境界条件を持たないケースのための基準圧力値。非圧縮性ソルバーのみ。

# 出力

この関数は、残差にアクセスするための `NamedTuple` を返します（例： `residuals.Ux`）で、以下のエントリがあります：

  * `Ux`  - 各イテレーションのx-速度残差のベクトル。
  * `Uy`  - 各イテレーションのy-速度残差のベクトル。
  * `Uz`  - 各イテレーションのy-速度残差のベクトル。
  * `p`   - 各イテレーションの圧力残差のベクトル。
