```
run!(
    model::Physics{T,F,M,Tu,E,D,BI}, config;
    output=VTK(), pref=nothing, ncorrectors=0, inner_loops=0
    ) where{T<:Steady,F<:Incompressible,M,Tu,E,D,BI} = 
begin
    residuals = simple!(model, config, pref=pref)
    return residuals
end
```

不圧縮定常ソルバーをSIMPLEアルゴリズムを使用して呼び出します。

# 入力

  * `model` はユーザーによって定義された `Physics` モデルを表します。
  * `config` はユーザーによって定義された構成構造体で、ソルバー、スキーム、ランタイム、およびハードウェア構造の構成詳細を含みます。
  * `output` はシミュレーション結果に使用される形式を `VTK()` または `OpenFOAM()` から選択します（デフォルト = `VTK()`）。
  * `pref` は圧力を定義するBCを持たないケースのための基準圧力値です。不圧縮ソルバーのみ。

# 出力

この関数は残差にアクセスするための `NamedTuple` を返します（例： `residuals.Ux`）で、以下のエントリがあります：

  * `Ux`  - 各イテレーションのx-速度残差のベクトル。
  * `Uy`  - 各イテレーションのy-速度残差のベクトル。
  * `Uz`  - 各イテレーションのy-速度残差のベクトル。
  * `p`   - 各イテレーションの圧力残差のベクトル。
