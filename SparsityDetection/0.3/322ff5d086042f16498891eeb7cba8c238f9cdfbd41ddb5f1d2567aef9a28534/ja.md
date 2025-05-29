# SparsityDetection.jl

#### 注意: このリポジトリは、同様にコードを検査し、スパースパターンを検出できる ModelingToolkit.jl に取って代わられました。

[![Build Status](https://github.com/SciML/SparsityDetection.jl/workflows/CI/badge.svg)](https://github.com/SciML/SparsityDetection.jl/actions?query=workflow%3ACI)

これは、Julia 関数に対する自動ヤコビアンおよびヘッセ行列のスパースパターン検出のためのパッケージです。数値計算のために書かれた関数は、スパース性を理解し、利用するために自動的に調査されることができます。これは数値的には機能せず、代わりに非標準の解釈によって、正確なスパースパターンを決定するために接続性のためにすべての分岐をチェックします。

このパッケージを使用する場合は、以下を引用してください：

```
@article{gowda2019sparsity,
  title={Sparsity Programming: Automated Sparsity-Aware Optimizations in Differentiable Programming},
  author={Gowda, Shashi and Ma, Yingbo and Churavy, Valentin and Edelman, Alan and Rackauckas, Christopher},
  year={2019}
}
```

## 例

次の関数があるとします。

```julia
fcalls = 0
function f(dx,x)
  global fcalls += 1
  for i in 2:length(x)-1
    dx[i] = x[i-1] - 2x[i] + x[i+1]
  end
  dx[1] = -2x[1] + x[2]
  dx[end] = x[end-1] - 2x[end]
  nothing
end
```

この関数に対して、ヤコビアンのスパースパターンが `Tridiagonal` 行列であることがわかっています。しかし、ヤコビアンのスパースパターンがわからない場合は、`jacobian_sparsity` 関数を使用して自動的にスパースパターンを検出できます。この関数は、Cassette.jl をロードした場合にのみ利用可能です。関数 `f` が長さ 30 のベクトルを出力し、長さ 30 のベクトルを入力として受け取ることを宣言し、`jacobian_sparsity` は `Sparsity` オブジェクトを出力し、それを `SparseMatrixCSC` に変換できます：

```julia
using SparsityDetection, SparseArrays
input = rand(10)
output = similar(input)
sparsity_pattern = jacobian_sparsity(f,output,input)
jac = Float64.(sparse(sparsity_pattern))

```

## API

### ヤコビアンのスパース性

自動ヤコビアンのスパース性検出は、`sparsity!` 関数によって提供されます。構文は次のとおりです：

```julia
jacobian_sparsity(f, Y, X, args...; sparsity=Sparsity(length(X), length(Y)), verbose=true)
```

引数は次のとおりです：

  * `f`: 関数
  * `Y`: 出力配列
  * `X`: 入力配列
  * `args`: `f` へのトレーリング引数。`Fixed(arg)` としてラップされない限り、変更される可能性があります。
  * `S`: (オプション) スパースパターン
  * `verbose`: (オプション) スパース性検出によって取られたパスを説明するかどうか。

関数 `f` は、`f(dx,x,args...)` の形式の引数を取ると仮定されます。`jacobian_sparsity` は、ヤコビアンの非ゼロがどこにあるかを説明する `Sparsity` オブジェクトを返します。`sparse(::Sparsity)` は、パターンをスパース行列に変換します。

この関数は、非標準の解釈を利用しており、これを組合せ的コノリック分析と呼び、プログラムの AST から直接スパースパターンを実現します。関数 `f` が Julia 関数である必要があります。これは数値的には機能せず、浮動小数点エラーやキャンセルに対して脆弱ではありません。分岐を許可し、すべての分岐を自動的にチェックします。ただし、入力引数に依存する不確定長の while ループは許可されていません。

### ヘッセ行列のスパース性

```julia
hessian_sparsity(f, X, args...; verbose=true)
```

引数は次のとおりです：

  * `f`: 関数
  * `X`: 入力配列
  * `args`: `f` へのトレーリング引数。`Fixed(arg)` としてラップされない限り、変更される可能性があります。
  * `verbose`: (オプション) スパース性検出によって取られたパスを説明するかどうか。

関数 `f` は、`f(x,args...)` の形式の引数を取り、スカラーを返すと仮定されます。

この関数は、非標準の解釈を利用しており、これを組合せ的コノリック分析と呼び、プログラムの AST から直接スパースパターンを実現します。関数 `f` が Julia 関数である必要があります。これは数値的には機能せず、浮動小数点エラーやキャンセルに対して脆弱ではありません。分岐を許可し、すべての分岐を自動的にチェックします。ただし、入力引数に依存する不確定長の while ループは許可されていません。
