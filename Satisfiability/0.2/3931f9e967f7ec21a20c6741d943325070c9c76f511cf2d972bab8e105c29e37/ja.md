```
smt(z::AbstractExpr)
smt(z1,...,zn; assert=true)
smt([z1,...,zn]; assert=true, line_ending='
```

', as_list=true)

`z`または`and(z1,...,zn)`のSMT表現を生成します。

`smt([z1,...,zn])`を呼び出すとき、配列は`Array{AbstractExpr}`型でなければなりません。リスト内包表記は配列の型を保持しないことに注意してください。例えば、`z`が`BoolExpr`の配列である場合、`[z[i] for i=1:n]`は`Any`型の配列になります。正しい型を保持するには、`BoolExpr[z[i] for i=1:n]`を使用してください。

オプションのキーワード引数は次のとおりです：

1. `assert = true|false`: デフォルトは`true`です。式が真でなければならないことを主張する（assert ...）SMT-LIB文を生成するかどうか。このオプションは、`smt`がブール式に対して呼び出された場合のみ有効です。
2. `line_ending`: 設定されていない場合、Windowsではデフォルトで"

"、それ以外の場所では' 'になります。

3. `as_list = true|false`: デフォルトは`false`です。`true`の場合、`smt`は単一の`line_ending`で区切られた文字列の代わりにコマンドのリストを返します。

```
