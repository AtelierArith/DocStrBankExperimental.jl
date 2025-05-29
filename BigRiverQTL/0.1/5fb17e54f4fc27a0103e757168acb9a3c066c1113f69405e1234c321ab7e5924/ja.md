get*loco*geno(dfG::DataFrame; chromosome*colname::String = "Chr", idx*start::Int = 5)

染色体に基づいて遺伝子型行列のベクトルを返します。

# 引数

  * `dfG` は、染色体、遺伝子座などの遺伝子型値と遺伝子型情報を含むデータフレームです。
  * `chromosome_colname` は、染色体情報を含む列名です。
  * `idx_start` は、遺伝子型値を含む最初の列インデックスを示します。
