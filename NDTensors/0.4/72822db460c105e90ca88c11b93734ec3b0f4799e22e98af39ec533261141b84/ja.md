blockview(T::DiagBlockSparseTensor, block::Block)

ブロックオフセットリスト内のブロックを指定すると、そのブロック内のデータへのビューであるDiagテンソルを返します（位置が既に知られている場合、ブロックの検索を避けるため）。
