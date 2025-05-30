```
waterflows(dem, cellarea=fill!(similar(dem),1), flowdir_fn=d8dir_feature;
           feedback_fn=nothing, drain_pits=true, bnd_as_sink=false)
```

水の流れはD8アルゴリズムに従ってルーティングされます。`dem`の`NaN`値を持つ場所は無視されます。

args:

  * dem – DEM（または水文学的ポテンシャル）；配列
  * cellarea=cellarea=fill!(similar(dem),1) – セルごとのソース、デフォルトは1。

      * もしcellareaが場所によって負であれば、フラックスはゼロに達することはあってもそれ以下にはなりません。
      * ルーティングが行われない領域、通常はdemのNaNにおいて、cellareaは無視されます。これは質量保存に影響を与える可能性があります。
      * 物理単位を使用する場合は、セルごとの体積フラックスを使用してください。例：m3/s。
      * あるいは、`cellarea`は配列のタプルであることもできます。その場合、それらは別々に処理/ルーティングされます。例えば、`(water, tracer)`。すべての量は広がりのあるものである必要があります（すなわち加算可能で、内部エネルギーを使用し温度ではない）。
  * flowdir*fn=d8dir*feature – ルーティング関数。デフォルトは組み込みの`d8dir_feature`関数ですが、カスタマイズ可能です。

kwargs:

  * feedback*fn – 各セルの水がすべて蓄積された後、しかし水がさらに下流にルーティングされる前に、各セルの面積値に適用される関数。シグネチャ`(uparea, ij, dir) -> new*uparea`--> 例えば、`(uparea, ij, dir) -> max(uparea, 0)`はすべての上流面積が非負であることを保証します。
  * drain_pits – ピットを通してルーティングするかどうか（true）
  * bnd*as*sink (true) – ドメイン境界がシンクであるべきか、すなわち隣接するセルがそれに排水できるか、または無視するか。
  * nan*as*sink (true) – DEMのNaNセルが隣接するセルをシンクにするべきか。
  * stacksize (2^13 * 2^10) – *flowrouting*catchments!におけるコールスタックのサイズで、StackOverflowErrorが発生しやすいです。ただし、増加させるとOutOfMemoryエラーが発生する可能性が高いことに注意してください。

Returns

  * area – 上流面積（またはcellareaがタプルの場合は上流面積のタプル）
  * stream-length – 最も遠いソースまでの流れの長さ（通過したセルの数）
  * dir – 各位置での流れの方向
  * nout – ポイントに流出があるかどうか。すなわち、nout[I]==0 –> Iはピット
  * nin – 流入セルの数
  * sinks – シンクの位置を示すVector{CartesianIndex{2}}
  * pits – ピットの位置を示すVector{CartesianIndex{2}}
  * c – 集水域マップ（色番号∈ 1:length(sinks)はシンク用、他はピット用）
  * bnds – 集水域間の境界。外部/NaNsへの境界はここには含まれません。
  * flowdir*extra*output – flowdir_fnの追加出力で、デフォルトでは`nothing`です。

```
