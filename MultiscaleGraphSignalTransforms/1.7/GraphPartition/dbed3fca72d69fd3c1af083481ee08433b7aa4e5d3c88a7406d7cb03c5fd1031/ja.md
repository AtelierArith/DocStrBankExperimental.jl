```
GP = GraphPart(ind::Vector{Int}, rs::Matrix{Int}, tag::Matrix{Int}, compinfo::Matrix{Int}, rsf2c::Matrix{Int}, tagf2c::Matrix{Int}, compinfof2c::Matrix{Int}, inds::Matrix{Int}, method::Vector{Symbol})
```

は、次のフィールドを含むGraphPartオブジェクトのデータ構造です：

  * `ind::Vector{Int}`: 最も細かいレベルでのインデックスの順序
  * `rs::Matrix{Int}`: regionstarInt (粗から細へ) <==> 領域番号 `i` の最初の点の `ind` におけるインデックスは `rs[i]`
  * `tag::Matrix{Int}`: GHWT粗から細への基底のタグ情報
  * `compinfo::Matrix{Int}`: 係数が2つのcoefficenIntから形成されたか（値は非ゼロ）または1つの係数からのみ形成されたか（値はゼロ）を示す；スケーリングとHaarのような係数が形成されると、それに対応するcompinfoの値は2つのサブリージョンの各ノードの数を示します
  * `rsf2c::Matrix{Int}`: `rs`の細から粗へのバージョン
  * `tagf2c::Matrix{Int}`: `tag`の細から粗へのバージョン
  * `compinfof2c::Matrix{Int}`: `compinfo`の細から粗へのバージョン
  * `inds::Matrix{Int}`: すべてのレベルでのインデックスの順序
  * `method::Symbol`: パーティションツリーがどのように構築されたか

符号なし整数は、基盤となるグラフのサイズに依存します。

著作権 2015 カリフォルニア大学のRegenInt

実装者: Jeff Irion (アドバイザー: Dr. Naoki Saito) | 翻訳および修正: Naoki Saito, 2017年2月7日 2つのパラメータ用に修正: Naoki Saito, 2017年2月24日
