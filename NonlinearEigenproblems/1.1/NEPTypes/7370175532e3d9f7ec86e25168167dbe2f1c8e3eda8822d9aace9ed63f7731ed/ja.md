```
Mder_Mlincomb_NEP(n,Mder_fun, [maxder_Mder,] Mlincomb_fun, [maxder_Mlincomb])
```

`Mder_fun` と `Mlincomb_fun` の関数ハンドルによって定義された `compute_Mder` と `compute_Mlincomb` から `NEP` を作成します。`Mlincomb_fun(λ,X)` はスカラー `λ::Number` と行列 `X` の2つのパラメータを取ります。サイズ `n::Int` も指定する必要があります。関数 `Mlincomb_fun(λ,X)` は、X内のベクトルと掛け合わされた導関数の線形結合に対応するベクトルを返す必要があります。実装されている導関数の数が限られている場合は、`maxder_Mder` または `maxder_Mlincomb` を設定する必要があります。例えば、導関数が実装されていない場合は、`maxder=0` に設定します。

`Mder_NEP` も参照してください。

注意: これは便利な関数ですが、高性能計算には推奨されません。例えば、型の安定性を維持しないためです。

# 例

以下の例は、外部関数で定義された線形固有値問題 `A0+λA1` を定義します。

```julia-repl
julia> using LinearAlgebra; # I関数のため
julia> function my_Mder(s,der)
    A0=ones(Float64,3,3)-I; A0[1,1]=-1;
    A1=ones(Float64,3,3)*3; A1[2,3]=0;
    if (der==0)
       return A0+A1*s;
    elseif (der==1)
       return A1;
    else
       return zero(A0);
    end
end
julia> function my_Mlincomb(s,X) # 導関数の線形結合を計算
    A0=ones(Float64,3,3)-I; A0[1,1]=-1;
    A1=ones(Float64,3,3)*3; A1[2,3]=0;
    if (size(X,2) <= 1)
       return A0*X[:,1]+s*A1*X[:,1]
    else # これは: size(X,2) => 2 を意味します
       return A0*X[:,1]+A1*(s*X[:,1]+X[:,2]);
    end
end
julia> nep=Mder_Mlincomb_NEP(3,my_Mder,my_Mlincomb);
julia> (λ,v)=augnewton(nep,v=[1.0; 2.3; 0.0])
julia> norm(compute_Mder(nep,λ)*v)
6.798699777552591e-17
```
