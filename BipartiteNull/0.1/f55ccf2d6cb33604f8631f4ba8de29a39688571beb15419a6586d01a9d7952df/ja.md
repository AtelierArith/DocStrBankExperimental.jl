`LinksPerSpecies(data::DataFrame)`

種ごとのリンクの合計を種の数で割ったもの（全体および個別の状況を考慮）。

# 引数

  * `data`:二部ネットワークの隣接行列。

# 戻り値

  * `all`:全ての種の数で割ったリンクの合計。
  * `agroup`:行の種の数で割ったリンクの合計。
  * `bgroup`:列の種の数で割ったリンクの合計。

# 例

using BipartiteNull,DataFrames;

data=ExampleData(6);

print(data);

all,agroup,bgroup=LinksPerSpecies(data)
