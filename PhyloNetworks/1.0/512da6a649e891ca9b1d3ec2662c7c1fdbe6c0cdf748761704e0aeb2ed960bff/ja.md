```
nni!(αu::Edge, u::Node, uv::Edge, v::Node, vδ::Edge)
nni!(αu,u,uv,v,vδ, flip::Bool, inner::Bool, indices)
```

焦点エッジ `uv` の周りでネットワークをローカルに変形する NNI を実行します。これは、u-β を切り離し、vδ に接ぎ木します：

```
α - u -- v ------ δ
    |    |
    β    γ

α ------ v -- u - δ
         |    |
         γ    β
```

`flip` ブール値は、uv エッジが反転したかどうかを示し、`inner` ブール値はエッジ αu と uv の両方がノード u に向かっているかどうかを示します。すなわち、α->u<-v<-δ の場合です。これが真であれば、αu と vδ のハイブリッド状態を反転させます。

`indices` は、ノードとエッジの u*in*αu、αu*in*u、vδ*in*v、および v*in*vδ のインデックスを提供します。これらは次のように解釈されます：

```
u_in_αu: エッジ αu における u のインデックス
αu_in_u: ノード u における αu のインデックス
vδ_in_v: ノード v における vδ のインデックス
v_in_vδ: エッジ vδ における v のインデックス
```

**警告**：

  * *隣接性の確認は行いません*
  * 対称性のおかげで必要ないケース（`nni!(vδ, v, uv, u, αu)` や `nni!(βu, u, v, vγ)` でカバーされるケースなど）については実装されていません。具体的には、これらのケースは実装されておらず（チェックもされていません）：

      * u がハイブリッドでなく、v がハイブリッド
      * u がハイブリッドで、v がハイブリッドでなく、α -> u <- v -> δ
  * このため、`nni(αu,u,uv,v,vδ, ...)` は直接使用しないでください。代わりに `nni!(uv, move_number)` を使用してください。
  * nni!(undoinfo...) はトポロジーを復元しますが、ハイブリッドノードの下にあるエッジは、以前はそうでなかった場合でも長さ 0.0 になります。

ノード番号とエッジ番号は変更されません。エッジ `uv` は、その方向が α -> u -> v -> δ または α <- u <- v <- δ の場合を除いて、方向を変更せずに保持されます。この場合、`uv` の方向は反転します。

2 番目のバージョンの入力は出力と同じシグネチャを持ちますが、NNI をより簡単に元に戻します。これは、`output = nni!(input)` の場合、`nni!(output...)` が有効であり、最初の操作を元に戻すことを意味します。

現在、ブランチの長さはハイブリッドノードの下にある場合を除いて変更されません。将来のバージョンでは、ブランチの長さを変更するオプションが実装されるかもしれません。
