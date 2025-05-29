```
オプション
```

モデルオブジェクトの動作や定義を制御するオプションを表すキーと値のペアのコレクションです。キーはオプション名で、常にシンボルであり、シンボルに変換されますが、値は何でもかまいません。

オプションはドット表記を使用してアクセスできます。関数 [`getoption`](@ref) と [`setoption!`](@ref) も提供されています。これらは、オプション名が有効なJulia識別子でない場合にも、オプションのプログラム的処理に使用できます。

関連情報: [`Options`](@ref), [`getoption`](@ref), [`getoption!`](@ref), [`setoption!`](@ref)

# 例

```jldoctest
julia> o = Options(maxiter=20, tol=1e-7)
Options:
    maxiter=20
    tol=1.0e-7

julia> o.maxiter = 25
25

julia> o
Options:
    maxiter=25
    tol=1.0e-7

```
