NaNを注入するためのパラメータを記述する構造体

## フィールド

  * `active::Boolean` trueの場合のみ注入
  * `value::Any` 注入する値; 通常は`NaN`または`Inf`
  * `n_inject::Int` 注入する最大NaN数; NaNが注入されるたびに減少
  * `odds::Int` 1:oddsの確率でNaNを注入—値が高いほど注入が稀になる
  * `functions::Array{FunctionRef}` 指定されている場合、これらの関数内でのみNaNを注入; デフォルトは関数に対して差別しない
  * `libraries::Array{String}` 指定されている場合、このライブラリ内でのみNaNを注入。

    **注意**: ライブラリには`.jl`サフィックスを含めてはいけません—デフォルトではライブラリ名を探す際にそのサフィックスを削除するため、ここに含めると決して一致しません。
  * `record::String` 指定されている場合、注入の出来事を後で`replay`引数で再生できるように記録します。
  * `replay::String` 指定されている場合、すべての以前の指示を無視し、このファイルを注入再生に使用します。

`functions`と`libraries`は共にユニオンとして機能します: すなわち、可能なNaN注入ポイントの集合は`functions`と`libraries`によって一致する場所のユニオンです。
