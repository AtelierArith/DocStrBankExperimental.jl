```
update = ParamUpdate(conf, param_lists...)
```

`conf` によって構成された更新を返し、`param_lists` で定義されたパラメータのセットに適用されます。

`param_lists` の各要素は、生成関数とそのパラメータ参照のベクターのペアです。

**例**。生成関数 `foo` のパラメータ `:a` と `:b`、および生成関数 `:bar` のパラメータ `:theta` に勾配降下更新を適用する更新を構築するには：

```julia
update = ParamUpdate(GradientDescent(0.001, 100), foo => [:a, :b], bar => [:theta])
```

---

上記のコンストラクタ形式の構文糖。

```
update = ParamUpdate(conf, gen_fn::GenerativeFunction)
```

与えられた生成関数が所有するすべての学習可能なパラメータに適用される、`conf` によって構成された更新を返します。

与えられた生成関数が所有していない学習可能なパラメータは、関数の実行中に使用されていても更新されません。

**例**。生成関数 `foo` がパラメータ `:a` と `:b` を持つ場合、パラメータ `:a` と `:b` に勾配降下更新を適用する更新を構築するには：

```julia
update = ParamUpdate(GradientDescent(0.001, 100), foo)
```
