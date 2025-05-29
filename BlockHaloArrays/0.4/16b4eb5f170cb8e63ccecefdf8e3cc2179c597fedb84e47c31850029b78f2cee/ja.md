ブロックが境界にあるかどうかを判断します

# 引数

  * `A::AbstractBlockHaloArray`: 問題の配列
  * `blockid::Integer`: ブロックのID。このIDは通常スレッドIDに関連付けられています
  * `boundary::Symbol`: どの境界をチェックしていますか？例としては:ilo, :jhiなどがあります...
