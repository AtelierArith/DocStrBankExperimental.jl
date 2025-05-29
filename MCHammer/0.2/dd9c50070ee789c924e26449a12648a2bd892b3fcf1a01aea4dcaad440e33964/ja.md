Crawford学習曲線法。

```
struct CrawfordMethod <: LearningCurveMethod end
```

オペレーションズリサーチで見られる離散累積コスト分析手法に基づいているCrawford学習曲線（例：Crawford, 1982）は、個々のユニットコストを集約します。これらのコストはユニットインデックスの冪法則関数に従って減少し、総コストを算出します。WrightやExperienceの滑らかな曲線とは異なり、Crawford法は生産シーケンスにおける位置に基づいて減少するユニットコストをユニットごとに合計します。

$$
\text{Cost} = \sum_{i=1}^{\text{TotalUnits}} \text{InitialEffort} \times i^{\frac{\log(\text{Learning})}{\log(2)}}
$$

**使用するタイミング：**

  * 詳細なユニットコストデータがあり、学習効果の粒度の高い離散分析が必要な場合。

**避けるべきタイミング：**

  * 全体的なコストトレンドが連続的で、滑らかな曲線で最もよく表現される場合。この場合、WrightモデルやExperienceモデルの方が好ましいかもしれません。
