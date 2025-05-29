```
transpose!(t::Transposition; waitall=true)
transpose!(dest::PencilArray{T,N}, src::PencilArray{T,N};
           method = Transpositions.PointToPoint())
```

データを1つのペンシル構成から別のペンシル構成に転置します。

最初のバリアントでは、MPI送信操作が完了するのを待つことをオプションで遅らせることができます。これは、呼び出し元がすでに受信したデータで他の操作を行いたい場合に便利です。これを行うには、呼び出し元は`waitall = false`を渡し、操作が完了したら`Transposition`オブジェクトに対して手動で[`MPI.Waitall`](@ref)を呼び出す必要があります。このオプションは、転置メソッドが`PointToPoint`のときにのみ効果があります。

詳細については、[`Transposition`](@ref)を参照してください。
