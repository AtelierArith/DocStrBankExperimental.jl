# `havel_hakimi_graph`

与えられた次数列を持つグラフを作成します

## 使用法

`A = havel_hakimi_graph(d)` は、次数列 d を持つグラフのインスタンスを返すか、次数列がグラフィカルでない場合は ArgumentError をスローします。

## 入力

  * `d::Vector{Int}`: 整数値の次数のベクトル

## 出力

-`A`: Havel-Hakimi 手法から得られる無向グラフのための行列ネットワーク。
