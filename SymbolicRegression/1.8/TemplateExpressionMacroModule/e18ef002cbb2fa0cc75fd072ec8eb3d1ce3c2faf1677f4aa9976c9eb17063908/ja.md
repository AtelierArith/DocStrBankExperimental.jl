```
@template_spec(
    parameters=(p1=10, p2=10, p3=1),
    expressions=(f, g),
) do x1, x2, class
    return p1[class] * g(x1^2) + f(x1, x2, p2[class]) - p3[1],
end
```

（実験的）指定されたパラメータと式を持つTemplateExpressionSpecを作成します。パラメータはインデックス可能な定数を定義するために使用され、式はテンプレート構造の関数キーを定義します。
