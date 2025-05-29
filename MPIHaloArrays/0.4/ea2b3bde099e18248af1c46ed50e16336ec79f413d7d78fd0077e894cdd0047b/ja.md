ヘルパー関数：ロウサイドハローおよびドメインの開始/終了インデックスを取得する

# 引数

  * `field`: 配列
  * `dim`: インデックスをチェックする次元
  * `nhalo`: ハローエントリの数

# 戻り値

  * `NTuple{Int, 4}`: ロウインデックスのセット (lo*halo*start, lo*halo*end, lo*domain*start, lo*domain*end)。
