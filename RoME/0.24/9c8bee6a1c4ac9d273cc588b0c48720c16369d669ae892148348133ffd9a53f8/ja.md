```julia
assembleChordsDict(dfg; ...)
assembleChordsDict(dfg, vsyms; MAXADI, lastPoseNum, chords)

```

因子グラフ内の連続するポーズ間の相対コードを計算します。データ構造はDict{Symbol,Dict{Symbol,Tuple{Matrix,Matrix}}}です。2つのMatrix値は3x100で、最初のものは添付されたスクリーンキャプチャに示されています。これらの値は、dict[:x0][:x1]、またはdict[:x0][:x2]、またはdict[:x0][:x2]など、合理的なコード長までのすべてのポーズに対する相対変換である必要があります。また、2つの行列値があります。最初のものは測定値のみに基づく相対変換であり、2番目の行列は、使用されているすべてのデータのSLAMソリューションに従った同じ相対変換です。
