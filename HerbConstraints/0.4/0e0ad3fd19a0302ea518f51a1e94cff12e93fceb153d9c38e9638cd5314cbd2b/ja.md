```
Forbidden <: AbstractGrammarConstraint
```

この [`AbstractGrammarConstraint`] は、`tree` で与えられたパターンに一致するサブツリーが生成されることを禁止します。パターンは [`AbstractRuleNode`](@ref) のツリーです。そのようなノードは、[`RuleNode`](@ref) であることができ、これは [`AbstractGrammar`](@ref) のルールインデックスに対応するルールインデックスと、[`RuleNode`](@ref) と同様の適切な数の子を含みます。また、単一の識別子シンボルを含む [`VarNode`](@ref) を含むこともできます。[`VarNode`](@ref) は任意のサブツリーに一致することができますが、パターン内に同じ変数の複数のインスタンスがある場合、一致したサブツリーは同一でなければなりません。一致を試みて成功するドメイン内の任意のルールは削除されます。

例えば、ツリー `1(a, 2(b, 3(c, 4))))` を考えてみましょう：

  * `Forbidden(RuleNode(3, [RuleNode(5), RuleNode(4)]))` は `c` に `5` を充填することを禁止します。
  * `Forbidden(RuleNode(3, [VarNode(:v), RuleNode(4)]))` は `c` に充填することを禁止します。なぜなら、[`VarNode`] は任意のルールに一致することができるため、`c` の全ドメインに対して一致を試みることが成功するからです。したがって、このツリーは無効です。
  * `Forbidden(RuleNode(3, [VarNode(:v), VarNode(:v)]))` は `c` に `4` を充填することを禁止します。なぜなら、それは `v` への両方の割り当てを等しくし、一致を成功させるからです。
