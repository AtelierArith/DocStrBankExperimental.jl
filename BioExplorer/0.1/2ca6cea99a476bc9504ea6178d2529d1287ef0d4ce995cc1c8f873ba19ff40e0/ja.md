```
octave(community_matrix::Community_Matrix, community_selected::String)
```

選択したコミュニティにおける種のオクターブ分布を計算します。

# 引数

  * `community_matrix::Community_Matrix`: 入力コミュニティ行列。
  * `community_selected::String`: オクターブ分布を計算するコミュニティの名前。

# 戻り値

タプル `(community_name, community_ranked)` を返します：

  * `community_name` は選択したコミュニティの名前です。
  * `community_octave` は種の豊富さとそれに対応するオクターブクラスを含む DataFrame です。

# 詳細

この関数は、入力コミュニティ行列から選択したコミュニティ内の種の豊富さのオクターブ分布を計算します。オクターブ分布は、種の豊富さをオクターブクラスに分類し、各クラスは豊富さの倍増を表します。

他にも [`octave_plot`](@ref) を参照してください、
