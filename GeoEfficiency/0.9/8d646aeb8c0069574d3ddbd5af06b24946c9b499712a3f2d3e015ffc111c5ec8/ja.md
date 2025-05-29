```
WellDetector(CryRadius::Real, CryLength::Real, HoleRadius::Real, HoleDepth::Real)
```

指定された結晶の寸法に基づいて `Well-Type` 検出器を構築して返します：

  * `CryRadius` : 検出器結晶の半径。
  * `CryLength` : 検出器結晶の長さ。
  * `HoleRadius` : 検出器の穴の半径。
  * `HoleDepth` : 検出器の穴の長さ。

!!! warning
    すべての引数は `正` の数である必要があります。また、 `CryRadius` は `HoleRadius` より大きく、 `CryLength` は `HoleDepth` より大きくする必要があります。

