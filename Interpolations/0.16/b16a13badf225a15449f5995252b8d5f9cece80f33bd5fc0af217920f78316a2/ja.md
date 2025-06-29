`extrapolate(itp, scheme)` は、提供されたスキームに従って補間オブジェクトに外挿動作を追加します。

スキームは次のいずれかの値を取ることができます：

  * `Throw` - 範囲外のインデックスに対して BoundsError をスローします
  * `Flat` - 最も近い範囲内の値を取る定数外挿
  * `Line` - 線形外挿（ラップされた補間オブジェクトは勾配をサポートしている必要があります）
  * `Reflect` - 反射外挿（インデックスは `mod` をサポートしている必要があります）
  * `Periodic` - 周期的外挿（インデックスは `mod` をサポートしている必要があります）

スキームをタプルで組み合わせることもできます。たとえば、スキーム `(Line(), Flat())` は、最初の次元で線形外挿を使用し、2 番目の次元で定数を使用します。

最後に、異なる方向で異なる外挿動作を指定することもできます。`((Line(),Flat()), Flat())` は、インデックスが小さすぎる場合は最初の次元で線形外挿を行い、大きすぎる場合は定数外挿を使用し、常に2番目の次元で定数外挿を使用します。
