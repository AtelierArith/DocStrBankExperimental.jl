Wright学習曲線法。

```
struct WrightMethod <: LearningCurveMethod end
```

T.P. Wrightによって1936年に航空機生産コスト分析に関する彼の画期的な研究で導入されました（Wright, 1936）。このモデルは、累積生産が倍増するごとに、単位コストが固定の割合で減少することを観察します。これは、学習が継続的かつ徐々に進行するプロセスに適しています。

$$
\text{Cost} = \text{InitialEffort} \times \text{TotalUnits}^{\frac{\log(\text{Learning})}{\log(2)} + 1}
$$

**使用するタイミング：**

  * 歴史的データが生産が倍増するにつれて単位コストが滑らかで予測可能な減少を示す場合。

**避けるべきタイミング：**

  * コスト削減が離散的なステップで発生する場合や、生産プロセスが構造的な変化を経験する場合。
