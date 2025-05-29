ハイサイドハローとドメインの開始/終了インデックスを取得するためのヘルパー関数

# 引数

  * `field`: 配列
  * `dim`: インデックスを確認する次元
  * `nhalo`: ハローエントリの数

# 戻り値

  * `NTuple{Int, 4}`: loインデックスのセット (hi*domain*start, hi*domain*end, hi*halo*start, hi*halo*end)。
