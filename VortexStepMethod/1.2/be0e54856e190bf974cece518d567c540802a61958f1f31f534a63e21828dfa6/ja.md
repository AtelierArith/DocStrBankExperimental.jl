```
Wing(n_panels::Int;
     n_groups=n_panels,
     spanwise_distribution::PanelDistribution=LINEAR,
     spanwise_direction::PosVector=MVec3([0.0, 1.0, 0.0]),
     remove_nan::Bool=true)
```

デフォルト値を持つ[Wing](@ref)構造体のコンストラクタで、セクションと洗練されたセクションを空の配列として初期化します。

# パラメータ

  * `n_panels::Int`: 空力メッシュ内のパネルの数
  * `n_groups::Int`: 空力メッシュ内のパネルグループの数
  * `spanwise_distribution`::PanelDistribution = LINEAR: [PanelDistribution](@ref)
  * `spanwise_direction::MVec3` = MVec3([0.0, 1.0, 0.0]): 翼のスパン方向ベクトル
  * `remove_nan::Bool`: 補間からNaNを削除するかどうか
