```
XPRSgetstringattrib(prob, attrib, maxbytes)::value, nbytes
```

ユーザーがさまざまな文字列の問題属性の値を回復できるようにします。

問題属性は、問題の読み込みと最適化中に設定されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `attrib::Integer`: 値を返す問題属性。
  * `maxbytes::Integer`: cgval 引数に書き込む最大バイト数。

# 戻り値

  * `value::AbstractString`: 属性の値（およびヌル終端子）が返される文字列へのポインタ。
  * `nbytes::Int32`: ヌル終端子を含む文字列制御の長さを返します。

C API の対応する関数 [XPRSgetstringattrib](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetstringattrib.html) のドキュメントも参照してください。
