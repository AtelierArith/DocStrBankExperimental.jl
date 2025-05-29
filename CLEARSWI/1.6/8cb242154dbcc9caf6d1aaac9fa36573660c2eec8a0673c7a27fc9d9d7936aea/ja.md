```
calculateSWI(data::Data, options::Options=Options())
```

'data'と'options'を使用して計算されたSWIを返します。

# 例

```julia-repl
julia> TEs = [4,8,12]
julia> data = Data(mag, phase, header(mag), TEs);
julia> swi = calculateSWI(data);
```

# オプションを使用して

Base.Docs.DocStr(svec("    Options(;   mag*combine=:SNR,\n                mag*sens=nothing,\n                mag*softplus=true,\n                phase*unwrap=:laplacian,\n                phase*hp*sigma=[4,4,0],\n                phase*scaling*type=:tanh,\n                phase*scaling*strength=4,\n                writesteps=nothing)\n\n* `mag_combine`は、振幅のエコーの組み合わせを選択します。オプションは\n    * `:SNR`\n    * `:average`\n    * `:last`は最後のエコーを選択\n    * `(:CNR => (:gm, :wm))`は、現在7Tでのみ機能する`src/tissue.jl`で選択可能な組織クラスの間のコントラストを最適化します\n    * `(:echo => 3)`は3番目のエコーを選択\n    * `(:closest => 15.3)`は15.3 msに最も近いエコーを選択\n    * `(:SE => 15.3)`は15.3 msのエコー時間を持つ対応する単一エコースキャンを使用して達成されるコントラストをシミュレートします。\n\n* `mag_sens`が配列に設定されている場合、CLEAR-SWI感度推定の代わりに使用されます。これは`mag_sens=[1]`に設定して、感度補正を実質的に回避するための定数感度1を使用することもできます。期待されるバイアスフィールドサイズのsigma*mm値を変更するには、例えば`mag*sens=(:sigma*mm => 7)`に設定します。デフォルトは7mmです。\n\n* 結合された振幅のスケーリングをソフトプラス関数で無効にするには、`mag*softplus=false`を使用します。\n\n*`phase*unwrap`は`:laplacian`、`:romeo`、または`:laplacianslice`（スライスごとのラプラスアンラッピング）です。\n\n*`phase*hp*sigma`はハイパスフィルタリングに使用され、[x,y,z]次元のボクセルで指定されます。  \n\n*`phase*scaling*type`は位相マスクを作成するためのスケーリング関数で、`:tanh`または`:negativetanh`のシグモイドフィルタリング、または`:positive`、`:negative`、`:triangular`の従来のSWIアプリケーション用です。\n\n*`phase*scaling*strength`は作成された位相マスクの強度を調整します。より高い`phase*scaling*strength`は、より強い位相の外観を持ちます。従来のSWI`phase*scaling*type`では、位相マスクの乗算の数またはパワーに対応します。\n\n*`writesteps`を中間ステップを保存するパスに設定します。例えば、`writesteps=\"/tmp/clearswi*steps\"`。`nothing`に設定すると、中間ステップは保存されません。\n\n* `qsm`をtrueに設定します\n"), nothing, Dict{Symbol, Any}(:typesig => Union{}, :module => CLEARSWI, :linenumber => 20, :binding => CLEARSWI.Options, :path => "/home/terasaki/.julia/packages/CLEARSWI/TpwBe/src/utility.jl", :fields => Dict{Symbol, Any}()))

# 例

```julia-repl
julia> TEs = [4,8,12]
julia> data = Data(mag, phase, header(mag), TEs);
julia> options = Options(phase_hp_sigma=[10,10,5], mag_softplus=false)
julia> swi = calculateSWI(data, options);
```
