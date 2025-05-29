```
isinferred(output::Output, ruleset::Ruleset)
isinferred(output::Output, rules::Rule...)
```

カスタムルールが推論され、`applyrule`または`applyrule!`が実行されたときに戻り値の型が正しいかどうかをテストします。

型の安定性は、パフォーマンスのオーダーオブマグニチュードの改善をもたらすことがあります。
