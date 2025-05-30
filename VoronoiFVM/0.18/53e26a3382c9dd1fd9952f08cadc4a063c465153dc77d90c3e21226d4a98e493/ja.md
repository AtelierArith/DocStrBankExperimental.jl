```
check_allocs!(system,true_or_false)
```

アセンブリループでの時間のかかるアロケーションのチェックを有効/無効にします。デフォルトでは、このチェックはオフになっています。環境変数 `ENV["VORONOIFVM_CHECK_ALLOCS"]="true"` を設定することで、このデフォルトを変更できます。

行列のパターンが変わらない限り、このループでアロケーションが発生することはないはずです。チェックメソッドは行列パターンの変化を認識しています。その結果、アセンブリループでのアロケーションは主に物理コールバックにおける型の不安定性によるものです。詳細については、[こちら](../runexamples/#Performance-with-closures)の議論を参照してください。型の不安定性は、物理コールバック内の式に適用された `@time` マクロを使用してデバッグできます。

以下のケースは、問題の理由や可能な解決策を探るためのアイデアを提供します。

ケース 1: パラメータが値を変更し、Juliaが型について確信が持てない。

```julia
eps=1.0

flux(f,_u,edge)
    u=unkowns(edge,_u)
    f[1]=eps*(u[1,1]-[1,2])
end
... solve etc ...
eps=2.0
```

解決策: 型アノテーション `eps::Float64=...` を使用して、Juliaに意図を示します。この動作については、[Juliaのドキュメント](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-captured)で説明されています。

ケース 2: クロージャ内の変数がコールバックで導入された変数と同じ名前を持つ。

```julia
flux(f,_u,edge)
    u=unkowns(edge,_u)
    f[1]=(u[1,1]-[1,2])
end

... create etc ...

u=solve(...)
```

解決策: 例えば `u=solve()` を `sol=solve()` に名前を変更します。
