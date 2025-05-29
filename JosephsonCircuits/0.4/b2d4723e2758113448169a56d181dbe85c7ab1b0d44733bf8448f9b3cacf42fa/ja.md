```
hbsolve(ws, wp::NTuple{N,Number}, sources::Vector,
    Nmodulationharmonics::NTuple{M,Int}, Npumpharmonics::NTuple{N,Int},
    circuit, circuitdefs;dc = false, threewavemixing = false,
    fourwavemixing = true, maxintermodorder=Inf, iterations = 1000,
    ftol = 1e-8, switchofflinesearchtol = 1e-5, alphamin = 1e-4,
    symfreqvar = nothing, nbatches = Base.Threads.nthreads(),
    sorting = :number, returnS = true, returnSnoise = false, returnQE = true,
    returnCM = true, returnnodeflux = false, returnvoltage = false,
    returnnodefluxadjoint = false, returnvoltageadjoint = false,
    keyedarrays::Val{K} = Val(true), sensitivitynames::Vector{String} = String[],
    returnSsensitivity = false, returnZ = false, returnZadjoint = false,
    returnZsensitivity = false, returnZsensitivityadjoint = false,
    factorization = KLUfactorization()) where {N,M,K}
```

ハーモニックバランスソルバー、[`hbnlsolve`](@ref) および [`hblinsolve`](@ref) を呼び出します。これらは任意の数のモードとポートに対して機能し、三波混合および四波混合プロセスの両方に対応しています。詳細は [`hbnlsolve`](@ref) および [`hblinsolve`](@ref) を参照してください。

# 引数

  * `ws`: 信号の角周波数（Hz）で、例えば 2*pi*5.0e9 または 2*pi*(4.5:0.001:5.0)*1e9 のような値です。
  * `wp::NTuple{N,Number}`: 強いトーン（またはポンプ）の角周波数を含むタプルで、例えば (2*pi*5.0e9,) は 5 GHz の単一ポンプ、(2*pi*5.0e9,2*pi*6.0e9) は 5 GHz と 6 GHz のポンプを示します。周波数は非共鳴である必要があります。共鳴ポンプの場合、最も低いポンプ周波数をここに提供し、他のポンプは比率に等しいモードインデックスで `sources` に追加します。
  * `sources::Vector`: 各ソースのモードインデックス、ポート、および電流を指定する名前付きタプルのベクターです。名前付きタプルには mode、port、current という名前があります。mode はポンプのモードまたはハーモニックインデックスを指定するタプルで、port はポートを指定する整数、current は電流を指定する数値です。電流は複素数であることに注意してください。例えば、[(mode=(1,0),port=1,current=Ip1),(mode=(0,1),port=1,current=Ip2)] は、最初のポンプの周波数が 1*wp1 + 0*wp2 で、2 番目が 0*wp1+1*wp2 である 2 つのポンプを指定します。ここで wp1 は最初のポンプ周波数、wp2 は 2 番目のポンプ周波数です。両方のポンプはポート 1 に適用され、それぞれの電流は Ip1 と Ip2 です。
  * `Nmodulationharmonics::NTuple{M,Int}`: 信号とアイドラーのモード数を説明する整数のタプルです。
  * `Npumpharmonics::NTuple{N,Int}`: 各ポンプのためにシミュレーションするハーモニクスの数を説明する整数のタプルです。タプルの長さは非共鳴ポンプの数と等しくなければなりません。
  * `circuit`: 各コンポーネント名、最初のノード、2 番目のノード、およびコンポーネント値を含むタプルのベクターです。最初の 3 つは文字列でなければなりません。
  * `circuitdefs`: キーがシンボルまたはコンポーネント値のためのシンボリック変数で、値がコンポーネントの数値である辞書です。

# キーワード

  * `dc = false`: ハーモニックバランス分析に 0 周波数項を含めます。
  * `threewavemixing = false`: 三波混合プロセスをシミュレートします。
  * `fourwavemixing = true`: 四波混合プロセスをシミュレートします。
  * `maxintermodorder=Inf`: 各周波数に掛かる整数の絶対値の合計が `maxintermodorder` 以下であると定義される最大インターモード順序です。これは離散フーリエ空間のダイヤモンド切断を行います。
  * `iterations = 1000`: 非線形ソルバーがエラーを返す前の反復回数です。
  * `ftol = 1e-8`: 収束と見なす関数の許容誤差で、norm(F)/norm(x) < ftol または norm(F,Inf) <= ftol と定義されます。
  * `switchofflinesearchtol = 1e-5`: ニュートン法からラインサーチを切り替える際の関数の許容誤差です。収束が容易な関数の場合、これをゼロに設定するとシミュレーションが速くなります。
  * `alphamin = 1e-4`: ラインサーチに対する最小ステップサイズです。
  * `symfreqvar = nothing`: シンボリック周波数変数、例えば `w` です。
  * `nbatches = Base.Threads.nthreads()`: マルチスレッド用に信号周波数を分割するバッチの数です。シングルスレッド評価の場合は 1 に設定します。
  * `sorting = :number`: ノードを次のようにソートします:   `:name`: 文字列のベクターをソートします。これは常に機能しますが、"101" が "11" の前に来る結果になります。   `:number`: ノード文字列を整数に変換し、これでソートします（ノード名が整数に変換できない場合はエラーになります）。   `:none`: グラウンドノードを最初に配置する以外はソートを行いません。言い換えれば、ノードを `circuit` で見つかった順に並べます。
  * `returnS = true`: 線形化シミュレーションから散乱パラメータを返します。
  * `returnSnoise = false`: 線形化シミュレーションからノイズ散乱パラメータを返します。
  * `returnQE = true`: 線形化シミュレーションから量子効率を返します。
  * `returnCM = true`: 線形化シミュレーションから交換関係を返します。
  * `returnnodeflux = false`: 線形化シミュレーションからノードフラックスを返します。
  * `returnvoltage = false`: 線形化シミュレーションからノード電圧を返します。
  * `returnnodefluxadjoint = false`: 線形化随伴シミュレーションからノードフラックスを返します。
  * `returnvoltageadjoint = false`: 線形化随伴シミュレーションからノード電圧を返します。
  * `keyedarrays::Val{K} = Val(true)`: Val(true) の場合、出力行列とベクターをキー付き配列として返し、より直感的なインデックス付けを行います。Val(false) の場合、通常の行列とベクターを返します。
  * `sensitivitynames::Vector{String} = String[]`: 感度を返すコンポーネント名です（進行中）。
  * `returnSsensitivity = false`: 線形化シミュレーションから散乱パラメータ感度行列を返します（進行中）。
  * `returnZ = false`: 線形化シミュレーションからインピーダンス行列を返します。
  * `returnZadjoint = false`: 線形化随伴シミュレーションからインピーダンス行列を返します。
  * `returnZsensitivity = false`: 線形化シミュレーションから Z パラメータ感度行列を返します（進行中）。
  * `returnZsensitivityadjoint = false`: 線形化随伴シミュレーションから Z パラメータ感度行列を返します（進行中）。
  * `factorization = KLUfactorization()`: 非線形および線形化シミュレーションに使用する因数分解のタイプです。

# 戻り値

  * `HB`: ハーモニックバランス解を保持するシンプルな構造体です。詳細は [`HB`](@ref) を参照してください。

```
