```
BoreDetector(CryRadius::Real, CryLength::Real, HoleRadius::Real)
```

与えられた結晶の寸法の `bore-hole` 検出器を構築して返します：

  * `CryRadius` : 検出器結晶の半径。
  * `CryLength` : 検出器結晶の長さ。
  * `HoleRadius` : 検出器の穴の半径。

!!! warning
    `CryRadius` と `CryLength`、`HoleRadius` は `正` の数である必要があります。また、`CryRadius` は `HoleRadius` より大きい必要があります。

