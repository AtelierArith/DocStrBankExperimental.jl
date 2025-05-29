```
@template_spec(
    expressions=(f, g, ...),
    [parameters=(p1=size1, p2=size2, ...)],
    [num_features=(f=n1, g=n2, ...)]
) do x1, x2, ...
    # テンプレート関数の本体
end
```

カスタムテンプレート構造を持つTemplateExpressionSpecを作成します。

このマクロは、サブ式の制約された構成とパラメータ化されたコンポーネントを持つ構造化された記号式を定義することを可能にします。

# 引数

  * `expressions`: テンプレート内で構成される関数名のタプル。
  * `parameters`: オプション。パラメータ名-サイズペアの名前付きタプル。これらのパラメータは、テンプレート関数内でインデックス付けされ、アクセスされることができます。
  * `num_features`: オプション。各式関数がアクセスできる特徴の数を指定する名前付きタプル。通常、これはテンプレート関数から自動的に推測されます。

# 例

```julia
expr_spec = @template_spec(
    parameters=(p1=10, p2=10, p3=1),
    expressions=(f, g),
) do x1, x2, class
    return p1[class] * g(x1^2) + f(x1, x2, p2[class]) - p3[1]
end
```
