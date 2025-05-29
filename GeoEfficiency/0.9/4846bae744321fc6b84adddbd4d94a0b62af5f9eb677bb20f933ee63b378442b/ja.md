```
CylDetector(CryRadius::Real, CryLength::Real)
```

与えられた結晶の寸法に基づいて `cylindrical` 検出器を構築して返します：

  * `CryRadius` : 検出器結晶の半径。
  * `CryLength` : 検出器結晶の長さ。

!!! warning
    `CryRadius` と `CryLength` は両方とも `positive` である必要がありますが、`CryLength` は **`zero`** に設定することもできます。

