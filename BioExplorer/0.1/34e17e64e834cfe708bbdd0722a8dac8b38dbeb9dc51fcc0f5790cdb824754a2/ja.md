```
whittacker_plot(community_matrix::Community_Matrix, community_selected::String)
```

選択したコミュニティのウィッタカー図を表示します。

# 引数

  * `community_matrix::Community_Matrix`: 入力コミュニティマトリックス。
  * `community_selected::String`: ウィッタカー図を表示するコミュニティの名前。

# 戻り値

  * ウィッタカー図を表すMakie Figure。

# 詳細

この関数は、入力コミュニティマトリックスから選択したコミュニティのウィッタカー図を生成します。プロットは、種の対数10の豊富さをそのランクに対して示します。種は豊富さによってランク付けされ、豊富さはy軸に対数10スケールでプロットされます。各種のランクはx軸にプロットされます。

他にも[`rank`](@re)、[`octave_plot`](@ref)を参照してください。
