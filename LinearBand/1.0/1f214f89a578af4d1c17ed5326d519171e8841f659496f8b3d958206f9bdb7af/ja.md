```
(band,height,tmin) = linearband(t, y, tmin_constraint; minheightfrac=0.8, 
								variableheight=false)
```

データ（`t`、`y`）の周りに区分線形バンドを計算します。

バンドは、データを囲む近似ミニマックス連続区分線形バンドです。このバンドの任意のセグメントの傾きが隣接するセグメントの傾きの間にない場合、その中線の長さは`tmin_constraint`未満にはなりません。返される値`tmin`は、実際の解におけるその最小長さであり、返される値`height`はバンドの最大高さです。出力`band`はタプル（LB、UB）です。バンドの下限は、mx2行列LB（最初の列はt値、2列目はy値）内の点を接続することによって定義され、上限はnx2行列UBによって定義されます。バンドは一定の高さを持つことも、各線形セグメントが独自の高さを持つこともあります（`varableheight=true`の場合）。一定の高さのバンドが要求される場合、LBとUBの両方のt値は同一になりますが、可変高さの場合、mがnと異なる可能性があります。いずれの場合も、LBとUBの最初の列の最初と最後の値は、入力`t`の最初と最後の値と同じになります。

変数`minheightfrac`は、分割できない最大高さのセグメントが見つかった後に、セグメントの分割がどの程度行われるかを制御します。高さが`minheightfrac*height`を超えるセグメントは分割されます。`variableheight=false`の場合、すべてのセグメントは制約セグメントと同じ高さになるように垂直に拡張されますが、その結果、より滑らかな外観のバンドになります。

`y`が行列の場合、バンドは各列iに対して（`t`、`y[:,i]`）に対して実行されます。入力`tmin_constraint`は、`y`の各列に対して異なるエントリを持つベクトルであるか、すべての列に適用されるスカラー値である可能性があります。`y`が行列の場合、出力`band`、`height`、および`tmin`はそれぞれベクトルであり、`y`の各列に対して1つのエントリがあります。

# 例

```julia-repl
julia> t = range(0.0,10.0,50); y = @. sin(t) + 0.2*cos(7*t);
julia> (band,height,tmin) = linearband(t,y,0.4);
julia> height
0.3776184236760187
julia> p=plot(t,y,seriescolor=:blue,markersize=2,seriestype=:scatter);
julia> (LB,UB) = band;
julia> plot!(p,LB[:,1],LB[:,2],seriescolor=:red);
julia> plot!(p,UB[:,1],UB[:,2],seriescolor=:red);
julia> gui(p)
```

# 拡張ヘルプ

このアルゴリズムは、Emily K. Szusz、Allan R. Willms、2010年の「離散データの近似ミニマックス連続区分線形表現のための線形時間アルゴリズム」、*SIAM J. Sci. Comput.* 32 (5)、pp. 2584-2602、doi=10.1137/090769077に記載されています。

この実装は、論文の説明と比較してアルゴリズムにいくつかの調整を加えています。特に、隣接するセグメントの傾きの間にあるセグメントは飲み込まれることが許可されています。また、制約の違反が発生した場合、アルゴリズムは近くのセグメントを分割して、違反を逆転できるかどうかを確認します。そうでない場合、最小高さは違反を引き起こした分割の高さと見なされます。その後、アルゴリズムは最小高さの`minheightfrac`まで、より低いバンドの分割を続けることができます。

Dr. Allan R. Willms, Dept. of Mathematics and Statistics, University of Guelph, Guelph, ON N1G 2W1, Canada
