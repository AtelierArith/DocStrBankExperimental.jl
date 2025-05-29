```
replicant(FV; kwargs...) -> Vector{GMTdataset}
```

3Dボディを記述するFaces-Verticesデータセットを取り、N回複製します。各コピーに異なる色やスケールを割り当てるオプションがあります。最終的な結果は、複製されたボディを持つ単一のVector{GMTdataset}です。

### 引数

  * `FV`: 3Dボディを記述するFaces-Verticesデータセット。

### キーワード引数

  * `replicate`: 次のフィールドの1つ以上を持つNamedTuple：`centers`、コピーの中心を持つMx3行列；`zcolor`、長さ$size(centers, 1)$のベクトルで、`cmap`オプションと共に使用される変数を指定し、各コピーの色を割り当てます（デフォルトは$1:size(centers, 1)$）；`cmap`、GMTcptオブジェクト；`scales`、各コピーのスケールファクターを指定するスカラーまたは長さ$size(centers, 1)$のベクトル。
  * `replicate`: 各コピーの中心を持つMx3行列。
  * `replicate`: 行列とスカラーまたはベクトルを持つタプル。最初の要素は中心のMx3行列で、2番目はスケールファクター（またはファクターのベクトル）です。
  * `scales`: このファクターまたはスケールのベクトル（コピーの数と同じ長さ）でコピーをスケールします。
  * `view or perspective`: 複製の視点角度を設定します。デフォルトは`217.5/30`です。この視点から見えない表面要素は排除されます。

### 戻り値

複製されたボディを持つVector{GMTdataset}。通常、三角形化された表面です。

### 例

```julia
FV = sphere();
D  = replicant(FV, replicate=(centers=rand(10,3), scales=0.1));

または、プロットするには

viz(FV, replicate=(centers=rand(10,3)*10, scales=0.1))
```
