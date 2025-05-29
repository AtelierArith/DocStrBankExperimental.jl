```
XPRSslpgetcoefstr(prob, row, col, maxbytes)::factor, formula, nbytes
```

単一の行列係数を文字列の形式で取得します。

この関数の簡易版については、XPRSnlpgetformulastrを参照してください。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 係数の行インデックスを保持する整数。
  * `col::Integer`: 係数の列インデックスを保持する整数。
  * `maxbytes::Integer`: `formula`バッファの長さ。

# 戻り値

  * `factor::Float64`: 係数内の式を掛ける定数因子の値を受け取るための倍精度変数のアドレス。
  * `formula::AbstractString`: ファイルからの入力に使用されるのと同じ形式で式が配置される文字バッファ。
  * `nbytes::Int32`: ヌル終端子を含まない式の長さに設定されます。

C APIの対応する関数[XPRSslpgetcoefstr](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetcoefstr.html)のドキュメントも参照してください。
