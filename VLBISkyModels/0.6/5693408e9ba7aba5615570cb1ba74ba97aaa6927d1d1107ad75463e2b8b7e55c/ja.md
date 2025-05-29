Creates a [Kamruddin and Dexter](https://academic.oup.com/mnras/article/434/1/765/1005984) crescent model. This works by composing two disk models together.

# Arguments

  * `router`: 外側ディスクの半径
  * `rinner`: 内側ディスクの半径
  * `shift`: 内側ディスクの半径がどれだけシフトされるか（正の値は右方向）
  * `floor`: 内側ディスクのフロア 0 は内側の強度がゼロで、1 は大きなディスクを意味します。
