`make_orders_into_chunks` は、orders*to*use の各オーダーからスペクトルの領域を持つ ChunkList を返します。

# 引数

  * spectra<:AbstractSpectra
  * inst: デフォルト値を提供する Instrument trait

# オプションの引数

  * orders*to*use: Range または Array (orders*to*use(inst))
  * pixels*to*use: Ranges の配列 (各々が min*col から max*col まで)

または

  * min*col: (min*col_default(inst,order)) および
  * max*col: (max*col_default(inst,order))
