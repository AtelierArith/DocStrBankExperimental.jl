```
Mder_NEP(n,Mder_fun; maxder=max)
```

`Mder_fun`によって定義された`compute_Mder`関数から`NEP`を作成します。`Mder_fun(λ,der)`は、スカラー`λ::Number`と導関数番号`der`の2つのパラメータを取ります。サイズ`n::Int`も指定する必要があります。関数`Mder_fun(λ,der)`は、`der`番目の導関数に対応するn x n行列を返す必要があります。利用可能な導関数の数が限られている場合は、`maxder`を設定する必要があります。たとえば、導関数が実装されていない場合は、`maxder=0`に設定します。関数`compute_Mlicomb`は、`compute_Mlincomb_from_Mder`への（委任による）自動的に利用可能です。

注意: これは便利な関数ですが、高性能計算には推奨されません。たとえば、型の安定性を維持しません。

# 例

以下の例では、外部関数で定義された線形固有値問題`A0+λA1`を定義します。

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
julia> nep=Mder_NEP(3,my_Mder);
julia> (λ,v)=augnewton(nep,v=ones(3));
julia> norm(compute_Mder(nep,λ)*v)
5.551115123125783e-17
```
