ContinuousTransitionノードの関数形式は次のように与えられます: y ~ Normal(K(a) * x, W⁻¹)

このノードは、m次元ベクトルxを、ベクトルaから変換K(a)を介して構築されたn×m次元行列Aを用いた線形（または非線形）変換を通じてn次元ベクトルyに変換します。ContinuousTransitionノードは主に2つのレジームで使用されます。

# Aに構造が指定されていない場合:

```julia
transformation = a -> reshape(a, 2, 2)
...
a ~ MvNormalMeanCovariance(zeros(2), Diagonal(ones(2)))
y ~ ContinuousTransition(x, a, W) where {meta = CTMeta(transformation)}
...
```

# Aに何らかの構造が知られている場合:

```julia
transformation = a -> [cos(a[1]) -sin(a[1]); sin(a[1]) cos(a[1])]
...
a ~ MvNormalMeanCovariance(zeros(1), Diagonal(ones(1)))
y ~ ContinuousTransition(x, a, W) where {meta = CTMeta(transformation)}
...
```

行列Aを構築するために、aの要素はメタで提供された変換関数に従ってAに再形成されます。単変量ガウス分布を使用する場合は、長さ1のベクトルとして使用してください。例: a ~ MvNormalMeanCovariance([0.0], [1.;])。

変換関数を指定する方法の詳細については、ContinuousTransitionMetaを確認してください。この関数は**必ず**行列を返す必要があります。

```julia
y ~ ContinuousTransition(x, a, W) where {meta = ContinuousTransitionMeta(transformation)}
```

インターフェース:

1. y - ContinuousTransitionノードのn次元出力。
2. x - ContinuousTransitionノードのm次元入力。
3. a - 行列Aにキャストされる任意次元ベクトル。
4. W - 遷移を和らげ、変分メッセージパッシングを行うために使用されるn×n次元精度行列。

Wを固定値に設定するか、事前分布を置いてジッターの量を制御することができます。

ContinuousTransitionノードは2つの因子分解をサポートしています。

1. 平均場因子分解:

```julia
@constraints begin
    q(y, x, a, W) = q(y)q(x)q(a)q(W)
end
```

2. 構造化因子分解:

```julia
@constraints begin
    q(y, x, a, W) = q(y, x)q(a)q(W)
end
```
