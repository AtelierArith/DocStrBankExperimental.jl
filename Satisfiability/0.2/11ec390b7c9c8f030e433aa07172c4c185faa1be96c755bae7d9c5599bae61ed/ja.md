```
output = "(
(define-fun x () Bool true)
(define-fun y () Bool false)
(define-fun f ((x!0 Bool)) Bool (ite (= x!0 false) true false))"
dict = parse_model(output)
```

`(get-model)`のSMT-LIB形式の出力を解析し、名前と値のDictを返します。値は正しい型になります。したがって、例では`dict["x"]`は`true`になります。未解釈の関数値はJulia関数自体になります。したがって、`dict["f"]`はBoolを受け取り、Boolを返す関数です。

この関数は主に`InteractiveSolver`を使用する際に便利です。
