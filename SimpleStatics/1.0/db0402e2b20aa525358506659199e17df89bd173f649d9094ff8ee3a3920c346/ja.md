```
plot_setup(setup, [name]; [dsize=800, padding, displacements, stresses, reactions])
```

# 引数

  * `setup::StaticSetup`: プロットするセットアップ。
  * `name::String`: 作成する画像のファイル名またはパス（拡張子なし）。指定しない場合、画像は返されますが保存されません。
  * `dsize::Integer`: 画像の対角ピクセルサイズ。実際の幅と高さはプロットされるセットアップによって異なります。
  * `padding::Float64`: セットアップ境界の周囲に含める追加の距離。0のパディングは画像をできるだけ小さくし、詳細が画面外に出てしまう可能性があります。デフォルトは0.4です。

# 含めることができる追加の詳細。

  * `displacements`: `solve_displacements`を使用して以前に計算された変位。
  * `member_forces`: `solve_member_forces`を使用して以前に計算されたメンバー力。
  * `reactions`: `solve_reaction_forces`を使用して以前に計算された反応力。
