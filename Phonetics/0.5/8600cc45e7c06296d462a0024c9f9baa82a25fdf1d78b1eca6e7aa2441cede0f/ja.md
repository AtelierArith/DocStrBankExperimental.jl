```
avgseq(S; [method=:dtw, dist=SqEuclidean(), radius=10, center=:medoid, dtwradius=nothing, progress=false])
```

`S`内のシーケンスの平均をdbaメソッドを使用して表すシーケンスを返します。シーケンスの比較を行う際に、`method=:dtw`で通常のdtw、`method=:fastdtw`で高速dtw近似をサポートします。`center=:medoid`を使用すると、初期中心として使用するシーケンスをメドイドとして見つけ、`center=:rand`を使用すると、`S`内のランダムな要素を初期中心として選択します。

# 引数

  * `S` 平均を取るシーケンスの配列
  * `method` (キーワード) 使用する動的時間ワーピングのメソッド
  * `dist` (キーワード) `Distances`パッケージの`SemiMetric`インターフェースを実装する任意の距離関数
  * `radius` (キーワード) 高速dtwメソッドに使用する半径; method=:dtwのときは引数は未使用
  * `center` (キーワード) `S`内のシーケンスの初期中心を選択するために使用されるメソッド
  * `dtwradius` (キーワード) シーケンスを比較する際に時間ステップがどれだけマッピングできるか; `DynamicAxisWarping`の`DTW`関数に直接渡される; `nothing`に設定すると、最長シーケンスの長さが使用され、実質的に半径制限が解除される
  * `progress` `dba`からの進行状況を表示するかどうか
