```
abstract type CombinatorialObjective
```

組合せ問題のための特定の目的関数。一般的に、目的は自然な目的関数を最小化または最大化することですが、他のサブタイプでより具体的な目的を提供することもできます。

`CombinatorialObjective`型のオブジェクトは、`CombinatorialInstance`を構築する際に引数として与えられるべきです。いずれにせよ、`objective(::CombinatorialInstance)`を使用してインスタンスの目的を取得できます。
