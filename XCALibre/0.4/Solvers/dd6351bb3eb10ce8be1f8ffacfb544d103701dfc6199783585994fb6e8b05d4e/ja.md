```
cpiso!(model, config; 
    output=VTK(), pref=nothing, ncorrectors=0, inner_loops=0)
```

結合された運動量と質量保存方程式を解くためのSIMPLEアルゴリズムの非圧縮性および過渡的バリアント。

# 入力引数

  * `model` ユーザーによって定義された`Physics`モデルへの参照。
  * `config` ユーザーによって定義された構成構造体で、ソルバー、スキーム、ランタイムおよびハードウェア構造の構成詳細。
  * `output` シミュレーション結果に使用される形式を`VTK()`または`OpenFOAM`から選択します（デフォルト = `VTK()`）
  * `pref` 圧力を定義するBCを持たないケースのための基準圧力値。非圧縮性ソルバーのみ（デフォルト = `nothing`）
  * `ncorrectors` 非直交性補正ループの数（デフォルト = `0`）
  * `inner_loops` PISOアルゴリズムに基づく過渡ソルバーで使用される内部ループの数（デフォルト = `0`）

# 出力

  * `Ux` 各反復のx-速度残差のベクトル。
  * `Uy` 各反復のy-速度残差のベクトル。
  * `Uz` 各反復のy-速度残差のベクトル。
  * `p` 各反復の圧力残差のベクトル。
