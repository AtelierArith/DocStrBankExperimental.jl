```
CrudeMortality
```

このメソッドは粗死亡率を計算し、過剰死亡率と人口死亡率の両方を提示します。

デフォルトのCronin-Feuer推定量は、以下のインターフェースを使用してデータにフィットさせることができます：

```
fit(CrudeMortality, args...)
```

ここで、`args`は過剰ハザードを計算するために`fit(EdererII,args...)`に渡されます。

過剰ハザードの推定量を直接指定するより直接的な構文を使用することもできます：

```
CrudeMortality(fit(EdererII,args...))
```

別の過剰ハザード推定量を使用するには、単に`EdererII`をお好みの方法（`PoharPerme`、`EdererI`、`Hakulinen`）に置き換えればよいです。

参考文献：

  * [cronin2000cumulative](@cite) Cronin, Kathleen A と Feuer, Eric J (2000). 他の原因が存在するがん患者のための累積原因特異的死亡率：相対生存の粗い類似物。
