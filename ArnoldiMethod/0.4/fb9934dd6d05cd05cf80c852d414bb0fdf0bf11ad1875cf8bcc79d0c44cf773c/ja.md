```julia
partialschur(A; v1, workspace, nev, which, tol, mindim, maxdim, restarts) → PartialSchur, History
```

`A`の近くにある`nev`の近似固有対を見つけます。

行列`A`は、`mul!(y, A, x)`、`eltype`、および`size`を実装する任意の線形マップであることができます。

このメソッドは、固有対が指定された許容誤差に近似されるまで、または`restarts`の再起動が行われるまで、反復的に実行されます。

## 引数

最も重要なキーワード引数：

|   キーワード | 型                   | デフォルト                | 説明                                  |
| -------:|:------------------- |:-------------------- |:----------------------------------- |
|   `nev` | `Int`               | `min(6, size(A, 1))` | 固有値の数                               |
| `which` | `Symbol`または`Target` | `:LM`                | `:LM`、`:LR`、`:SR`、`:LI`、`:SI`のいずれか。 |
|   `tol` | `Real`              | `√eps`               | 収束の許容誤差: ‖Ax - xλ‖₂ < tol * ‖λ‖     |
|    `v1` | `AbstractVector`    | `nothing`            | Krylov部分空間のためのオプションの開始ベクトル          |

初期ベクトル`v1`について: それは変更されず、正規化する必要はありません。

ターゲット`which`は次のいずれかであることができます：

|          ターゲット | 説明                  |
| --------------:|:------------------- |
| `:LM`または`LM()` | 最大の絶対値: `abs(λ)`が最大 |
| `:LR`または`LR()` | 最大の実部: `real(λ)`が最大 |
| `:SR`または`SR()` | 最小の実部: `real(λ)`が最小 |
| `:LI`または`LI()` | 最大の虚部: `imag(λ)`が最大 |
| `:SI`または`SI()` | 最小の虚部: `imag(λ)`が最小 |

ArnoldiMethod v0.4以降、シンボルを使用したくない場合は、`using ArnoldiMethod: LM`を明示的にインポートする必要があります。

!!! note
    ターゲット`:LI`と`:SI`は複素数算術でのみ意味があります。実数算術では、`λ`が固有値であるのは`conj(λ)`が固有値である場合であり、この共役ペアは同時に収束します。


## 戻り値

関数はタプルを返します

```julia
decomp, history = partialschur(A, ...)
```

ここで、`decomp`は[`PartialSchur`](@ref)構造体で、指定された許容誤差で`A`の部分シュール分解を形成します：

```julia
> norm(A * decomp.Q - decomp.Q * decomp.R)
```

`history`は[`History`](@ref)構造体で、メソッドの収束に関する基本情報を保持します：

```julia
> history.converged
true
> @show history
359回の行列-ベクトル積の後に収束
```

## 高度な使用法

さらに、アルゴリズムを調整するための高度なキーワード引数があります：

|      キーワード | 型     | デフォルト                           | 説明                 |
| ----------:|:----- |:------------------------------- |:------------------ |
|   `mindim` | `Int` | `min(max(10, nev), size(A,1))`  | 最小Krylov次元 (≥ nev) |
|   `maxdim` | `Int` | `min(max(20, 2nev), size(A,1))` | 最大Krylov次元 (≥ min) |
| `restarts` | `Int` | `200`                           | 最大再起動回数            |

アルゴリズムが収束しない場合は、`restarts`を増やすことができます。アルゴリズムが収束するのが遅すぎる場合は、`mindim`と`maxdim`を調整できます。`mindim`は`nev`と等しいか、わずかに大きいことが推奨され、`maxdim`は通常`mindim`の約2倍です。
