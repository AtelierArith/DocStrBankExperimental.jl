```
hblinsolve(w, circuit, circuitdefs; Nmodulationharmonics = (0,),
    nonlinear=nothing, symfreqvar=nothing, threewavemixing=false,
    fourwavemixing=true, maxintermodorder=Inf,
    nbatches::Integer = Base.Threads.nthreads(), returnS = true,
    returnSnoise = false, returnQE = true, returnCM = true,
    returnnodeflux = false, returnnodefluxadjoint = false,
    returnvoltage = false,
    )

非線形の周りで線形化された任意の数の小信号（弱いトーン）をサポートする調和バランスソルバーで、非線形システムの解は `hbnlsolve` からの任意の数の大信号（強いトーン）で構成されます。

# 引数

  * `w`: 小信号の周波数または周波数の配列。
  * `circuit`: 各タプルがコンポーネント名、最初のノード、2番目のノード、およびコンポーネント値を含むタプルのベクター。最初の3つは文字列でなければなりません。
  * `circuitdefs`: キーがコンポーネント値のシンボルまたはシンボリック変数であり、値がコンポーネントの数値である辞書。

# キーワード

  * `Nmodulationharmonics::NTuple{M,Int}`: 信号とアイドラーのモードの数を説明する整数のタプル。
  * `nonlinear=nothing`: `hbnlsolve` からの非線形システムの解。
  * `symfreqvar = nothing`: シンボリック周波数変数、例えば `w`。
  * `threewavemixing = false`: 三波混合プロセスをシミュレートします。
  * `fourwavemixing = true`: 四波混合プロセスをシミュレートします。
  * `maxintermodorder=Inf`: 各周波数を掛ける整数の絶対値の合計が `maxintermodorder` 以下であることを定義する最大インターモード順序。この操作は離散フーリエ空間のダイヤモンド切断を行います。
  * `nbatches = Base.Threads.nthreads()`: マルチスレッド用に信号周波数を分割するバッチの数。シングルスレッド評価のために1に設定します。
  * `sorting = :number`: ノードを次のようにソートします:   `:name`: 文字列のベクターをソートします。これは常に機能しますが、「101」が「11」の前に来るような結果になります。   `:number`: ノード文字列を整数に変換し、これらでソートします（ノード名を整数に変換できない場合はエラーになります）。   `:none`: グラウンドノードを最初に配置する以外はソートを行いません。言い換えれば、ノードを `circuit` で見つかった順序で並べます。
  * `returnS = true`: 線形化されたシミュレーションから散乱パラメータを返します。
  * `returnSnoise = false`: 線形化されたシミュレーションからノイズ散乱パラメータを返します。
  * `returnQE = true`: 線形化されたシミュレーションから量子効率を返します。
  * `returnCM = true`: 線形化されたシミュレーションから交換関係を返します。
  * `returnnodeflux = false`: 線形化されたシミュレーションからノードフラックスを返します。
  * `returnvoltage = false`: 線形化されたシミュレーションからノード電圧を返します。
  * `returnnodefluxadjoint = false`: 線形化された随伴シミュレーションからノードフラックスを返します。
  * `returnvoltageadjoint = false`: 線形化された随伴シミュレーションからノード電圧を返します。
  * `keyedarrays::Val{K} = Val(true)`: Val(true) の場合、出力行列とベクターをキー付き配列として返し、より直感的なインデックス付けを行います。Val(false) の場合、通常の行列とベクターを返します。
  * `sensitivitynames::Vector{String} = String[]`: 感度を返すコンポーネント名（進行中）。
  * `returnSsensitivity = false`: 線形化されたシミュレーションから散乱パラメータ感度行列を返します（進行中）。
  * `returnZ = false`: 線形化されたシミュレーションからインピーダンス行列を返します。
  * `returnZadjoint = false`: 線形化された随伴シミュレーションからインピーダンス行列を返します。
  * `returnZsensitivity = false`: 線形化されたシミュレーションからZパラメータ感度行列を返します（進行中）。
  * `returnZsensitivityadjoint = false`: 線形化された随伴シミュレーションからZパラメータ感度行列を返します（進行中）。
  * `factorization = KLUfactorization()`: 非線形および線形化されたシミュレーションに使用する因数分解のタイプ。

# 戻り値

  * `LinearizedHB`: 調和バランスの解を保持するシンプルな構造体。 [`LinearizedHB`](@ref) を参照してください。

# 例

```

jldoctest circuit = Tuple{String,String,String,Union{Complex{Float64},Symbol,Int64}}[] push!(circuit,("P1","1","0",1)) push!(circuit,("R1","1","0",:Rleft)) push!(circuit,("L1","1","0",:Lm))  push!(circuit,("K1","L1","L2",:K1)) push!(circuit,("C1","1","2",:Cc))  push!(circuit,("L2","2","3",:Lm))  push!(circuit,("Lj3","3","0",:Lj))  push!(circuit,("Lj4","2","0",:Lj))  push!(circuit,("C2","2","0",:Cj)) circuitdefs = Dict{Symbol,Complex{Float64}}(     :Lj =>2000e-12,     :Lm =>10e-12,     :Cc => 200.0e-15,     :Cj => 900e-15,     :Rleft => 50.0,     :Rright => 50.0,     :K1 => 0.9, )

Idc = 1e-6*0 Ip=5.0e-6 wp=2*pi*5e9 ws=2*pi*5.2e9 symfreqvar = nothing

# 変調設定

Npumpharmonics = (16,) Nmodulationharmonics = (2,) threewavemixing=false fourwavemixing=true

nonlinear=hbnlsolve(     (wp,),     Npumpharmonics,     [         (mode=(0,),port=1,current=Idc),         (mode=(1,),port=1,current=Ip),     ],     circuit,circuitdefs;dc=true,odd=fourwavemixing,even=threewavemixing)

linearized = JosephsonCircuits.hblinsolve(ws,     circuit, circuitdefs; Nmodulationharmonics = Nmodulationharmonics,     nonlinear = nonlinear, symfreqvar=nothing, threewavemixing=false,     fourwavemixing=true, returnnodeflux=true, keyedarrays = Val(false)) isapprox(linearized.nodeflux,     ComplexF64[9.901008591291e-12 - 6.40587007644028e-14im 2.164688307719963e-14 - 2.90852607344097e-16im 6.671563044645655e-14 - 8.585524364135119e-16im; 2.1633104519765224e-14 - 8.251861334047893e-16im 1.0099063486905209e-11 - 1.948847859339803e-13im -8.532003011745068e-15 + 3.234788465760295e-16im; 6.671648606599472e-14 + 7.892709980649199e-16im -8.53757633177974e-15 - 9.748395563374129e-17im 9.856580758892428e-12 + 5.859984004390703e-14im; 1.5888896262186103e-11 - 1.0303480614499543e-13im -2.557126237504446e-12 + 1.759201163407723e-14im -8.475819811683215e-12 + 5.3531443609574795e-14im; -2.5781681021577177e-13 + 4.757590640631487e-15im 2.36818731889176e-12 - 4.569646499606389e-14im 1.116372367616482e-13 - 2.039935997276492e-15im; -1.0210743447568219e-11 - 5.905490368441375e-14im 1.3377918536056493e-12 + 7.190105205618706e-15im 2.5392856657302323e-11 + 1.5143842454586225e-13im; 2.4781693042536835e-11 - 1.6057018472176702e-13im -2.5342360504077476e-12 + 1.7306764301173096e-14im -8.40554044664581e-12 + 5.269404591748149e-14im; -2.348528974341763e-13 + 3.949450668269274e-15im 1.1449271118157543e-11 - 2.2093702114766968e-13im 1.0261871618968225e-13 - 1.7240213938923877e-15im; -1.0140560031409567e-11 - 5.828587508192886e-14im 1.3288225860409326e-12 + 7.0954601524623594e-15im 3.423954321087654e-11 + 2.0403371894291513e-13im],     atol = 1e-6)

# 出力

true ```
