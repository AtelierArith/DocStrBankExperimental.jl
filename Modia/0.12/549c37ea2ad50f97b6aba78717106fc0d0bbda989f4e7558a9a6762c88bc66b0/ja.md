```
path = PTP_path(names; positions, v_max, a_max, startTime=0.0)
```

新しいパスオブジェクトを生成して、`positions[i,:]` から `positions[i+1,:]` へできるだけ速く移動します。`positions[i,:]` は [m] の絶対距離の平行移動位置のセットであるか、または [rad] の角度の回転位置である可能性があります。ロボティクスでは、このような動きはPTP（ポイント・ツー・ポイント）と呼ばれます。信号は、与えられた `positions` で速度がゼロであることを考慮して、信号 `names[j]` に対して最大許容速度 `v_max[j]` と最大許容加速度 `a_max[j]` があるため、これ以上速く移動することはできないように構成されています。

信号が2つ以上ある場合（つまり、`length(names) > 1`）、パスはすべての信号が加速、定速、減速の各フェーズで同じ期間にあるように構築されます。これは、信号のうちの1つがその限界に達している一方で、他の信号はエンドポイントが同じ瞬間に到達するように同期されていることを意味します。

例えば、これは信号が `positions[1,:]` で速度ゼロを持ち、1つの信号が最大許容加速度で加速され、他の信号が最大許容速度に達するまで加速されることを意味します。適切な瞬間に、1つの信号がその最大許容加速度の負の値で減速され、すべての信号が速度ゼロで `positions[2,:]` に到達します。

この要素は、例えばドライブトレインを制御するコントローラーのための基準信号を生成するのに役立ちます。または、与えられた加速度に従ってフランジを駆動するためにも使用されます。

# 例

```julia
using Modia
@usingModiaPlot

const ptp_path = PTP_path(["angle1", "angle2", "angle3"],
                          positions = [0.0 2.0 3.0;  # angle1=0.0, angle2=2.0, angle3=3.0
                                       0.5 3.0 4.0;
                                       0.8 1.5 0.3;
                                       0.2 1.5 0.8],
                          startTime = 0.1,
                          v_max = 2*ones(3),
                          a_max = 3*ones(3))
angles = zeros(3)
getPosition!(ptp_path, 0.5, angles)   # angles = [0.12, 2.24, 3.24]
path = getPath(ptp_path)
plot(path, ["angle1", "angle2", "angle3"])
```
