```
PencilFFTPlan{T,N} <: AbstractFFTs.Plan{T}
```

MPI分散データに対するN次元FFTベースの変換の計画で、入力データの型は`T`です。

---

```
PencilFFTPlan(p::Pencil, transforms; kwargs...)
```

指定された[`Pencil`](https://jipolanco.github.io/PencilArrays.jl/dev/Pencils/#PencilArrays.Pencils.Pencil)構成に従って、分散配列のための`PencilFFTPlan`を作成します。`transforms`の仕様や可能なキーワード引数の詳細については、以下のバリアントを参照してください。

---

```
PencilFFTPlan(
    A::PencilArray, transforms;
    fftw_flags = FFTW.ESTIMATE,
    fftw_timelimit = FFTW.NO_TIMELIMIT,
    permute_dims = Val(true),
    transpose_method = Transpositions.PointToPoint(),
    timer = timer(pencil(A)),
)
```

MPI分散`PencilArray`に対するN次元変換の計画を作成します。

# 拡張ヘルプ

これは、`A`と同じ特性（次元、MPI分解、メモリレイアウトなど）を持つ配列のための`PencilFFTPlan`を作成します。これにより、N次元のドメイン上のデータが記述されます。

## 変換

各次元に沿って適用される変換は、`transforms`引数によって指定されます。可能な変換は[`Transforms.AbstractTransform`](@ref)のサブタイプとして定義されており、[変換タイプ](@ref)にリストされています。この引数は次のいずれかである必要があります：

  * 各次元に沿って適用されるN個の変換のタプル。例えば、`transforms = (Transforms.R2R(FFTW.REDFT01), Transforms.RFFT(), Transforms.FFT())`；
  * すべての次元に沿って適用される単一の変換。入力は自動的にN個の同等の変換に展開されます。例えば、3次元配列の場合、`transforms = Transforms.RFFT()`は3D実数から複素数への変換を指定し、`(Transforms.RFFT(), Transforms.FFT(), Transforms.FFT())`を渡すのと同等です。

前方変換は左から右に適用されることに注意してください。最後の例では、最初の次元に沿って実数から複素数への変換（`RFFT`）が最初に行われ、その後、2番目と3番目の次元に沿って複素数から複素数への変換（`FFT`）が続きます。

## 入力データのレイアウト

入力`PencilArray`は次の制約を満たす必要があります：

  * 配列の次元は*入れ替えられてはならない*。これは`PencilArray`を構築する際のデフォルトです。
  * `M`次元のドメイン分解（`M < N`）の場合、入力配列は*最後のM次元*に沿って分解されている必要があります。例えば、3Dデータの2D分解の場合、分解された次元は`(2, 3)`でなければなりません。特に、最初の配列次元は*異なるMPIプロセス間で分散されてはならない*。

    PencilArraysパッケージでは、分解された次元は[`Pencil`](https://jipolanco.github.io/PencilArrays.jl/dev/Pencils/#PencilArrays.Pencils.Pencil)を構築する際に指定されます。
  * 要素の型は指定された変換と互換性がある必要があります。例えば、実数から複素数への変換（`Transforms.RFFT`）は、入力が実数浮動小数点値であることを要求します。他の変換、例えば`Transforms.R2R`は、実数と複素数のデータの両方を受け入れます。

## キーワード引数

  * キーワード引数`fftw_flags`と`fftw_timelimit`は、`FFTW`計画作成関数に渡されます（[`AbstractFFTs`ドキュメント](https://juliamath.github.io/AbstractFFTs.jl/stable/api/#AbstractFFTs.plan_fft)を参照）。
  * `permute_dims`は、出力データのインデックスを反転させるべきかどうかを決定します。例えば、入力データがグローバル次元`(Nx, Ny, Nz)`を持つ場合、複素数から複素数へのFFTの出力は次元`(Nz, Ny, Nx)`を持ちます。これにより、FFTは常に最初の（すなわち最も速い）配列次元に沿って実行されるため、パフォーマンスの向上が期待できます。このオプションはデフォルトで有効です。型推論の理由から、値型（`Val(true)`または`Val(false)`）である必要があります。
  * `transpose_method`は、グローバルデータの転置の実装を選択することを可能にします。詳細については[PencilArraysドキュメント](https://jipolanco.github.io/PencilArrays.jl/dev/Transpositions/#PencilArrays.Transpositions.Transposition)を参照してください。
  * `timer`は`TimerOutput`オブジェクトである必要があります。詳細については[パフォーマンスの測定](@ref PencilFFTs.measuring_performance)を参照してください。

---

```
PencilFFTPlan(
    dims_global::Dims{N}, transforms, proc_dims::Dims{M}, comm::MPI.Comm,
    [real_type = Float64]; extra_dims = (), kws...
)
```

N次元変換の計画を作成します。

# 拡張ヘルプ

`PencilArray`や`Pencil`を取る代わりに、このコンストラクタは入力データのグローバル次元を`size_global`引数を介して受け取ります。

データは`comm`コミュニケーター内のMPIプロセスに分散されます。分配は`proc_dims`の値に従って`M`次元（`M < N`）にわたって行われ、各次元に沿って配置するMPIプロセスの数を指定します。

返された計画で変換可能な`PencilArray`は、[`allocate_input`](@ref)を使用して作成できます。

## オプション引数

  * 浮動小数点精度は、デフォルトで`Float64`である`real_type`パラメータを設定することで選択できます。
  * `extra_dims`は、変換されない1つ以上の追加次元のサイズを指定するために使用できます。これらの次元は、配列の最も右側（すなわち最も遅い）インデックスに追加されます。使用のヒントについては、以下の**追加次元**を参照してください。
  * 他のコンストラクタについては、さらにキーワード引数があります。

## 追加次元

`extra_dims`の1つの可能な用途は、ベクトルまたはテンソル場の成分を記述することです。しかし、これは異なる種類の場（スカラー、ベクトルなど）ごとに異なる`PencilFFTPlan`を作成する必要があることを意味します。複数の計画の作成を避けるために、`allocate_input`](@ref)と[`allocate_output`](@ref)を使用して`PencilArray`のタプル（または配列）を作成する方が、より良い代替手段かもしれません。

`extra_dims`のもう1つの正当な使用法は、変換されず、MPIプロセス間で分割されない1つ以上の直交次元を指定することです。

## 例

実データの3D FFTを実行したいとします。データは8つのMPIプロセスにわたって2つの次元に沿って分解されます：

```julia
size_global = (64, 32, 128)  # 実入力データのサイズ

# 最初の次元に沿って実数から複素数への変換を行い、その後
# 他の次元に沿って複素数から複素数への変換を行います。
transforms = (Transforms.RFFT(), Transforms.FFT(), Transforms.FFT())
# transforms = Transforms.RFFT()  # これは上記の行と同等です

proc_dims = (4, 2)  # 2D分解
comm = MPI.COMM_WORLD

plan = PencilFFTPlan(size_global, transforms, proc_dims, comm)
```
