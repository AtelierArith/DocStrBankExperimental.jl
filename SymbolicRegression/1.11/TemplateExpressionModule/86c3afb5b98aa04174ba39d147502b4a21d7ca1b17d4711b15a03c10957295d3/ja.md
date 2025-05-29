```
TemplateStructure{K,E,NF} <: Function
```

`TemplateExpression`のための所定の構造を定義する構造体であり、異なるコンテキストで結果を定義する関数を含みます。

`K`パラメータは、内部表現を表す記号を指定するために使用されます。コンストラクタ`TemplateStructure{K}(...)`を使用して宣言されていない場合、`variable_constraints`の`NamedTuple`のキーがこれを推測するために使用されます。

`Kp`パラメータは、パラメータを表す記号を指定するために使用されます。

# フィールド

  * `combine`: `ComposableExpression`sの`NamedTuple`（キー`K`を共有）を受け取り、`ValidVector`sのデータを表すタプルを受け取る必須の関数です。例えば、`((; f, g), (x1, x2, x3)) -> f(x1, x2) + g(x3)`は有効な`combine`関数です。また、呼び出し可能な表現を再利用し、異なる入力を使用することもできます。例えば、`((; f, g), (x1, x2)) -> f(x1 + g(x2)) - g(x1)`も別の有効な選択です。
  * `num_features`: 各表現によって使用される特徴の数を表す整数への関数キーのオプションの`NamedTuple`です。提供されない場合、`combine`関数を使用して推測されます。例えば、`f`が2つの引数を取り、`g`が1つの引数を取る場合、`num_features = (; f=2, g=1)`となります。
  * `num_parameters`: 各パラメータベクトルに必要なパラメータの数を表す整数へのパラメータキーのオプションの`NamedTuple`です。
