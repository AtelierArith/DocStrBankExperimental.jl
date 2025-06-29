```
plotPath(path, plot::Function;
         names=path.names, heading="PTP プロット",
         tend=1.1*path.Tend, figure=1, ntime=101, onlyPositions=true)
```

`path::PTP_path` を与えられた場合、`names` ベクターまたはタプルで特定されたすべてのポイントについて、`tend` までの `time` に沿ってパスをプロットします。`ntime` 時間ポイントを使用して、`figure` にプロットします。

# 例

```julia
using ModiaLang
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
plotPath(ptp_path, plot)   # @usingModiaPlot で定義された plot(..) を使用
```
