```
ArpackOptions{T}(; nev=6, ncv=0, which=:LM,
                                       tol=zero(T),maxiter=300,
                                       v0=Vector{T}(0), have_v0=false,
                                       sigma=nothing)
```

は、アーノルディスキームを管理するオブジェクトを構築します。フィールドの意味については、`Arpack`パッケージの`eigs`に関するドキュメントを参照してください。
