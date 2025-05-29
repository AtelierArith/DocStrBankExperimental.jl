関数 `batch()` は、配置を指定するか指定しないかのいずれかで呼び出すことができます。引数なしのバージョンは、Microsoft Excel で簡単に編集できる事前に準備されたカンマ区切り値 [CSV] ファイルに依存しており、デフォルトでは **`/home/terasaki/GeoEfficiency`** ディレクトリにあります。

バッチ計算の結果は、検出器の名前が付けられた **`CSV`** ファイルに保存されます。デフォルトでは **`/home/terasaki/GeoEfficiency/results`** に **`CSV`** ファイルが見つかります。

# CSV 入力ファイル

  * `Detectors.csv` には検出器の説明が含まれています。行の形式は次のとおりです：

```
	 Crystal_Radius | Crystal_Length | Hole_Radius | Hole_Depth |
	 ---------------| ---------------|-------------|----------- |
```

  * `srcHeights.csv` にはソースの高さが含まれています；

```
	 Source_Heights | 
	 ---------------|
```

  * `srcRhos.csv` にはソースのオフアクシス距離が含まれています；

```
	 Source_Rhos | 
 	 ------------|
```

  * `srcRadii.csv` には円盤および円筒形ソースのソース半径が含まれています；

```
	 Source_Radii| 
	 ------------|
```

  * `srcLengths.csv` には円筒形ソースのソースの長さが含まれています；

```
	 Source_Lengths| 
	 --------------|
```

# CSV 結果ファイル

**`CSV`** ファイルには、`non-point` ソースのための `AnchorHeight`, `AnchorRho`, `srcRadius`, `srcLength`, `GeoEfficiency` のヘッダー列と、`point` ソースのための `Height`, `Rho`, `GeoEfficiency` のヘッダー列があります。

!!! 注     カンマ区切り値 [CSV] ファイルでは、各行はエントリを表し、最初の行は常にヘッダーとして扱われます。

!!! 警告     プログラムは、すべての CSV ファイルに対して各行に1つの数値が含まれていることを期待しますが、`Detectors.csv` については、各行には少なくとも1つの数値または最大4つの数値が区切られて含まれている必要があります。
