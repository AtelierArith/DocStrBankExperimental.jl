```
octave_plot(community_matrix::Community_Matrix, community_selected::String)
```

選択したコミュニティのオクターブプロットを表示します。

# 引数

  * `community_matrix::Community_Matrix`: 入力コミュニティマトリックス。
  * `community_selected::String`: オクターブプロットを表示するコミュニティの名前。

# 戻り値

  * オクターブプロットを表すMakie Figure。

# 詳細

この関数は、選択したコミュニティ内の種の豊富さのオクターブ分布を`octave`関数を使用して計算し、棒グラフとして表示します。プロット内の各棒はオクターブクラスを表し、x軸はオクターブクラスを、y軸は各オクターブクラスに該当する種の数を示します。

関連情報は[`octave`](@ref)を参照してください。
