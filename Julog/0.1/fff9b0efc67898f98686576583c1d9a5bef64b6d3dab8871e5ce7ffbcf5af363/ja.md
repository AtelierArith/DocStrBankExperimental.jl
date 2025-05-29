```
@julog expr
```

Julog式を解析して返します。

  * `@julog <term>` はPrologスタイルの項を解析します。
  * `@julog <term> <<= true` または `@julog <term>'` は事実（ボディなしの節）を解析します。
  * `@julog <head> <<= <body>` は確定節を解析します。
  * `@julog [<term|clause>, ...]` は項または節のベクターを解析します。
  * `@julog <T>[<term>, ...]` は型 `T`（例：`Const`）のベクターに解析します。
  * `@julog list[<term>, ...]` はPrologスタイルのリストを項に直接解析します。

さらに、`$` 演算子を使用して通常のJulia式をJulog定数として補間することができ、`:` 演算子を使用して事前に構築されたJulog項を参照する変数を別のJulog項または節に補間することができます。
