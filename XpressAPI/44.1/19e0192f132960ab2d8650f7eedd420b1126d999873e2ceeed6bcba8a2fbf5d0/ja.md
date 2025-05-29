```
XPRSgetstringcontrol(prob, control, maxbytes)::value, nbytes
```

指定された文字列制御パラメータの値を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `control::Integer`: 値を返す制御パラメータ。
  * `maxbytes::Integer`: 値引数に書き込む最大バイト数。

# 戻り値

  * `value::AbstractString`: 制御の値（およびヌル終端子）が返される文字列へのポインタ。
  * `nbytes::Int32`: ヌル終端子を含む文字列制御の長さを返します。

C APIの対応する関数[XPRSgetstringcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetstringcontrol.html)のドキュメントも参照してください。
