```
rank(community_matrix::Community_Matrix, community_selected::String)
```

選択したコミュニティにおける種の豊富さに基づいてランク付けします。

# 引数

  * `community_matrix::Community_Matrix`: 入力コミュニティマトリックス。
  * `community_selected::String`: 種のランク付けが必要なコミュニティの名前。

# 戻り値

タプル `(community_name, community_ranked)` を返します：

  * `community_name` は選択したコミュニティの名前です。
  * `community_ranked` は選択したコミュニティにおける豊富さでランク付けされた種を含む DataFrame です。

# 詳細

この関数は、入力コミュニティマトリックスの指定されたコミュニティにおける種の豊富さに基づいてランク付けを行います。種を豊富さの降順でソートし、ランクを割り当てます。同じ豊富さの種には同じランク（同点ランク）が割り当てられます。関数は豊富さがゼロの種を除外します。

関連情報は [`whittacker_plot`](@ref) を参照してください。
