```
fillsinks(G::GMTgrid; conn=4, region=nothing, saco=false, insitu=false)
```

グリッド内の沈殿物を埋めます。

この関数は、$imfill$関数を使用してグリッド内の沈殿物を埋める方法を見つけます。しかし、$imfill$はUInt8行列でのみ動作するため、グリッドの垂直（z）区分は256レベルに制限され、あまり多くはありません。

### 引数

  * `G::GMTgrid`: 処理する入力グリッド。

### キーワード引数

  * `conn::Int`: 沈殿物を埋めるための接続性（4または8）。デフォルトは4です。
  * `region`: `region`で指定されたグリッドの領域にアクションを制限します。例えば、$coast$マニュアルを参照してこのキーワードの拡張ドキュメントを確認してください。ただし、ここでは`region`のみが受け入れられ、`R`などは受け入れられません...
  * `saco::Bool`: 沈殿物を埋めるために使用された線（GMTdataset ~contours）を、GMT.SACOというグローバル変数に保存します。これは、関数が終了するたびにそれらをすべて返さないようにするためのものです。このグローバル変数は$[Dict{String,Union{AbstractArray, Vector{AbstractArray}}}()]$であるため、その内容にアクセスするには次のようにします：

    $$
    D = get(GMT.SACO[1], "saco", nothing)
    $$

    、ここで$D$は現在GMTdatasetまたはそれらのベクトルです。

    注意：このグローバル変数がもはや必要ない場合は、ユーザーの責任で空にする必要があります。

    それは次のように行います：$delete!(GMT.SACO[1], "saco")$
  * `insitu::Bool`: `true`の場合、グリッドをその場で変更します。デフォルトは`false`です。あるいは、従来の形式$fillsinks!(G; conn=4)$を使用します。

### 戻り値

  * 沈殿物が埋められた新しい`GMTgrid`、ただし`insitu`が`true`の場合は、入力グリッドが変更されて返されます。

### 例

```julia
G = peaks();
G2 = fillsinks(G);
viz(G2, shade=true)
```

今、埋めた輪郭を保存し、それらを重ねたプロットを作成します

```julia
G2 = fillsinks(G);
G2 = fillsinks(G, saco=true);
grdimage(G2)
plot!(get(GMT.SACO[1], "saco", nothing), color=:white, show=true)
```
