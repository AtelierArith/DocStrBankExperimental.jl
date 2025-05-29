```
asm2000(setting)
```

与えられた回帰設定に対して、Setan、Halim、Mohd (2000) アルゴリズムを実行します。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つ RegressionSetting オブジェクト。

# 説明

このアルゴリズムは、最小トリム二乗法 (LTS) 推定を実行し、標準化された残差 - フィッティング応答ペアを生成します。これらのペアに対して単一リンククラスタリングアルゴリズムが実行されます。`smr98` と同様に、クラスターツリーは Majona 基準を使用してカットされます。比較的小さな観測数を持つサブツリーは外れ値と見なされます。

# 出力

  * `["outliers"]`: 外れ値のインデックスのベクター。
  * `["betas"]`: 回帰係数のベクター。

# 例

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> asm2000(reg0001)
Dict{Any, Any} with 2 entries:
  "betas"    => [-63.4816, 1.30406]
  "outliers" => [15, 16, 17, 18, 19, 20]
```

# 参考文献

Robiah Adnan, Mohd Nor Mohamad, & Halim Setan (2001). 線形回帰における複数の外れ値の特定: ロバストフィットとクラスタリングアプローチ。マレーシア科学技術会議 2000 の議事録: シンポジウム C, Vol VI, (p. 400). マレーシア: マレーシア科学技術協会連合 COSTAM.
