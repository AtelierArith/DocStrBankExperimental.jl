```
dmrg(H::MPO, psi0::MPS; kwargs...)
dmrg(H::MPO, psi0::MPS, sweeps::Sweeps; kwargs...)
```

密度行列再正規化群（DMRG）アルゴリズムを使用して、行列積状態（MPS）を最適化し、エルミート行列 `H` の最小固有値の固有ベクトルとなるようにします。`H` は行列積演算子（MPO）として表現されます。

```
dmrg(Hs::Vector{MPO}, psi0::MPS; kwargs...)
dmrg(Hs::Vector{MPO}, psi0::MPS, sweeps::Sweeps; kwargs...)
```

密度行列再正規化群（DMRG）アルゴリズムを使用して、行列積状態（MPS）を最適化し、エルミート行列 `H` の最小固有値の固有ベクトルとなるようにします。このバージョンの `dmrg` は、`H` の表現としてMPOのベクトルを受け入れます。`Hs = [H1, H2, H3, ...]` として、`H` は `H = H1 + H2 + H3 + ...` と定義されます。このMPOの和は実際には計算されず、DMRGアルゴリズムの各ステップでMPOのセット `[H1,H2,H3,..]` が効率的にループされます。

```
dmrg(H::MPO, Ms::Vector{MPS}, psi0::MPS; weight=1.0, kwargs...)
dmrg(H::MPO, Ms::Vector{MPS}, psi0::MPS, sweeps::Sweeps; weight=1.0, kwargs...)
```

密度行列再正規化群（DMRG）アルゴリズムを使用して、行列積状態（MPS）を最適化し、エルミート行列 `H` の最小固有値の固有ベクトルとなるようにします。ただし、MPSはベクトル `Ms` に提供された各MPSに直交するという制約があります。直交性の制約は、`H` に `w|M1><M1| + w|M2><M2| + ...` の形の項を追加することでおおよそ強制されます。ここで `Ms=[M1, M2, ...]` であり、`w` は「重み」パラメータで、オプションの `weight` キーワード引数を通じて調整できます。

!!! note
    `dmrg` は演算子 `H + w|M1><M1| + w|M2><M2| + ...` のエネルギーを報告しますが、演算子 `H` のエネルギーではありません。MPS固有状態の `H` に関する期待値を取得したい場合は、観測者を使用するか、DMRGが実行された後に `inner(psi', H, psi)` で自分で計算できます。


MPS `psi0` は最適化されるMPSを初期化するために使用されます。

DMRGアルゴリズムのスイープ数は、`nsweeps` キーワード引数を渡すことで制御されます。キーワード引数 `maxdim`、`cutoff`、`noise`、および `mindim` も、アルゴリズムのコストと精度を制御するために渡すことができます - 詳細は以下を参照してください。

また、スイープ数と精度パラメータは `Sweeps` オブジェクトを通じて渡すこともできますが、このインターフェースはもはや推奨されていません。

返り値:

  * `energy::Number` - 最適化されたMPSの固有値
  * `psi::MPS` - 最適化されたMPS

キーワード引数:

  * `nsweeps::Int` - 実行するDMRGの「スイープ」数

オプションのキーワード引数:

  * `maxdim` - 最適化されるMPSのボンド次元またはランクの最大サイズを指定する整数または整数の配列。
  * `cutoff` - ボンド次元またはランクを切り捨てるために使用する切り捨て誤差のカットオフまたは閾値を指定する浮動小数点数または浮動小数点数の配列。
  * `eigsolve_krylovdim::Int = 3` - 固有値問題を局所的に解決するために使用されるクリロフ空間の最大次元。収束が遅い場合やハミルトニアンが臨界点に近い場合は、より高い値に設定してみてください。 [^krylovkit]
  * `eigsolve_tol::Number = 1e-14` - クリロフ固有ソルバーの許容誤差。 [^krylovkit]
  * `eigsolve_maxiter::Int = 1` - クリロフ部分空間を再構築できる回数。 [^krylovkit]
  * `eigsolve_verbosity::Int = 0` - クリロフソルバーの冗長性レベル。警告: これを有効にすると、ターミナルに多くの出力が表示されます。 [^krylovkit]
  * `ishermitian=true` - dmrgがMPO（またはより一般的な線形演算子）がエルミート行列を表すと仮定するかどうかを指定するブール値。 [^krylovkit]
  * `noise` - 収束を助けるために使用する「ノイズ項」の強さを指定する浮動小数点数または浮動小数点数の配列。
  * `mindim` - 可能であれば、ボンド次元またはランクの最小サイズを指定する整数または整数の配列。
  * `outputlevel::Int = 1` - 大きな出力レベル値はDMRGがより多くの情報を印刷し、0は出力なしを意味します。
  * `observer` - 測定を行い、DMRGを早期に停止できる [Observer](@ref observer) インターフェースを実装するオブジェクト。
  * `write_when_maxdim_exceeds::Int` - 許可されたmaxdimがこの値を超えた場合、大規模計算でRAMメモリを解放するためにテンソルをディスクに保存し始めます。
  * `write_path::String = tempdir()` - maxdimが `write_when_maxdim_exceeds` オプションを超えた場合にファイルをディスクに保存するために使用するパス（RAMを節約するため）。

[^krylovkit]: `ITensorMPS.jl` の `dmrg` 関数は現在、内部固有ソルバーとして `KrylovKit.jl` の `eigsolve` 関数を使用しています。詳細については、`KrylovKit.jl` の `eigsolve` 関数に関するドキュメントを参照してください: [KrylovKit.eigsolve](https://jutho.github.io/KrylovKit.jl/stable/man/eig/#KrylovKit.eigsolve).

```
