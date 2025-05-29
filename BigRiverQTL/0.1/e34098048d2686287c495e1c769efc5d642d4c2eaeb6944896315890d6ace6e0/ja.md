get*loco*geno*info(dfG::DataFrame; chromosome*colname::String = "Chr", idx_info = collect(1:4))

染色体に基づいて遺伝子型情報データフレームのベクトルを返します。

# 引数

  * `dfG` は遺伝子型値と染色体、ロキなどの遺伝子型情報を含むデータフレームです。
  * `chromosome_colname` は染色体情報を含む列名です。
  * `idx_info` は遺伝子型情報を含む列を示します（例：ローカス、Mb...）。
