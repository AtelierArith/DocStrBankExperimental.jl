```
hbnlsolve(w::NTuple{N,Number}, Nharmonics::NTuple{N,Int}, sources,
    circuit, circuitdefs; iterations = 1000,
    maxintermodorder = Inf, dc = false, odd = true, even = false,
    x0 = nothing, ftol = 1e-8, switchofflinesearchtol = 1e-5,
    alphamin = 1e-4, symfreqvar = nothing, sorting= :number)
```

任意の数の大信号（強いトーンまたはポンプ）と、ポート、ソース、ドライブの任意の数をサポートするハーモニックバランスソルバー。直流（ゼロ周波数）または電流源と相互インダクタを使用したフラックスポンピングを含みます。`hblinsolve`を使用して、`hbnlsolve`で見つけた動作点の周りで方程式のシステムを線形化します。

# 引数

  * `w::NTuple{N,Number}`: 強いトーン（またはポンプ）の角周波数を含むタプル。例えば、5 GHzの単一トーンの場合は(2*pi*5.0e9,)、5 GHzと6 GHzのトーンの場合は(2*pi*5.0e9,2*pi*6.0e9)です。周波数は非共鳴である必要があります。共鳴周波数の場合は、最も低い周波数をここに提供し、他の周波数は比率に等しいモードインデックスで`sources`に追加します。
  * `Nharmonics::NTuple{N,Int}`: 各トーンのためにシミュレーションするハーモニクスの数を記述する整数のタプル。タプルの長さは非共鳴トーンの数と等しくなければなりません。
  * `sources::Vector`: 各ソースのモードインデックス、ポート、および電流を指定する名前付きタプルのベクター。名前付きタプルには、mode、port、およびcurrentという名前があります。modeはポンプのモードまたはハーモニックインデックスを指定するタプルで、portはポートを指定する整数、currentは電流を指定する数です。電流は複素数であることに注意してください。例えば、[(mode=(1,0),port=1,current=Ip1),(mode=(0,1),port=1,current=Ip2)]は、最初のポンプの周波数が1*wp1 + 0*wp2で、2番目が0*wp1+1*wp2である2つのポンプを指定します。ここで、wp1は最初のポンプ周波数、wp2は2番目のポンプ周波数です。両方のポンプはポート1に適用され、電流はそれぞれIp1とIp2です。
  * `circuit`: 各コンポーネント名、最初のノード、2番目のノード、およびコンポーネント値を含むタプルのベクター。最初の3つは文字列でなければなりません。
  * `circuitdefs`: キーがコンポーネント値のシンボルまたはシンボリック変数で、値がコンポーネントの数値である辞書。

# キーワード

  * `iterations = 1000`: 非線形ソルバーがエラーを返す前の反復回数。
  * `maxintermodorder = Inf`: 各周波数に掛かる整数の絶対値の合計が`maxintermodorder`以下であることを定義する最大インターモード順。これは離散フーリエ空間のダイヤモンド切断を行います。
  * `dc = false`: ハーモニックバランス分析に0周波数項を含める。
  * `odd = true`: ハーモニックバランス分析に奇数項を含める。
  * `even = false`: ハーモニックバランス分析に偶数項を含める。
  * `x0 = nothing`: ノードフラックスの初期値。
  * `ftol = 1e-8`: 収束と見なす関数の許容誤差。これは、norm(F)/norm(x) < ftolまたはnorm(F,Inf) <= ftolとして定義されます。
  * `switchofflinesearchtol = 1e-5`:
  * `alphamin = 1e-4`: ニュートン法からラインサーチを伴うニュートン法に切り替えるときの関数の許容誤差。収束が容易な関数の場合、これをゼロに設定するとシミュレーションが速くなります。
  * `symfreqvar = nothing`: シンボリック周波数変数、例えば`w`。
  * `sorting = :number`: ノードを次のようにソートします:   `:name`: 文字列のベクターをソートします。これは常に機能しますが、「101」が「11」の前に来るような結果になります。   `:number`: ノード文字列を整数に変換し、これらでソートします（ノード名を整数に変換できない場合はエラーになります）。   `:none`: グラウンドノードを最初に配置する以外はソートを行いません。言い換えれば、ノードを`circuit`で見つかった順序で並べます。

# 戻り値

  * `NonlinearHB`: ハーモニックバランスソリューションを保持するシンプルな構造体。[`NonlinearHB`](@ref)を参照してください。

# 例

```jldoctest
circuit = Tuple{String,String,String,Union{Complex{Float64},Symbol,Int64}}[]
push!(circuit,("P1","1","0",1))
push!(circuit,("R1","1","0",:Rleft))
push!(circuit,("L1","1","0",:Lm)) 
push!(circuit,("K1","L1","L2",:K1))
push!(circuit,("C1","1","2",:Cc)) 
push!(circuit,("L2","2","3",:Lm)) 
push!(circuit,("Lj3","3","0",:Lj)) 
push!(circuit,("Lj4","2","0",:Lj)) 
push!(circuit,("C2","2","0",:Cj))
circuitdefs = Dict{Symbol,Complex{Float64}}(
    :Lj =>2000e-12,
    :Lm =>10e-12,
    :Cc => 200.0e-15,
    :Cj => 900e-15,
    :Rleft => 50.0,
    :Rright => 50.0,
    :K1 => 0.9,
)

Idc = 50e-5
Ip=0.0001e-6
wp=2*pi*5e9
Npumpmodes = 2
out=hbnlsolve(
    (wp,),
    (Npumpmodes,),
    [
        (mode=(0,),port=1,current=Idc),
        (mode=(1,),port=1,current=Ip),
    ],
    circuit,circuitdefs;dc=true,odd=true,even=false)
isapprox(out.nodeflux[:],
    ComplexF64[15.190314040027522 - 8.56492651167657e-24im, 2.991103820177504e-6 - 1.8501001011477133e-8im, -6.835392148510984 - 1.0356102442254259e-14im, 7.396422335315908e-6 - 4.5749403967992827e-8im, 6.835392148539885 - 1.0356102451770844e-14im, 1.008026285172782e-5 - 6.23498762664213e-8im],
    atol = 1e-6)

# 出力
true
```
