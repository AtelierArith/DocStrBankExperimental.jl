```
save_logoplot(pfm, background, save_name; dpi=65)
```

# 引数

  * `pfm::Matrix{Real}`: 位置頻度行列
  * `background::Vector{Real}`: A, C, G, T の背景確率
  * `save_name::String`: プロットを保存するパス/ファイルの名前

注意点

  * `pfm` は確率行列でなければなりません

      * 各列の合計は 1 でなければなりません
  * `background` は長さ 4 のベクトルでなければなりません

      * 確率のベクトルでなければなりません
      * `background` の合計は 1 でなければなりません

# 例

```julia

pfm =  [0.02  1.0  0.98  0.0   0.0   0.0   0.98  0.0   0.18  1.0
        0.98  0.0  0.02  0.19  0.0   0.96  0.01  0.89  0.03  0.0
        0.0   0.0  0.0   0.77  0.01  0.0   0.0   0.0   0.56  0.0
        0.0   0.0  0.0   0.04  0.99  0.04  0.01  0.11  0.23  0.0]

background = [0.25, 0.25, 0.25, 0.25]

#= tmp フォルダに logo.png としてロゴプロットを保存 =#
save_logoplot(pfm, background, "tmp/logo.png")

#= 現在のフォルダに logo.png として dpi 65 でロゴプロットを保存 =#
save_logoplot(pfm, background, "logo.png"; dpi=65)

```
