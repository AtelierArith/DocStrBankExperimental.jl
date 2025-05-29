`SigAction`はCの`struct sigaction`構造体の対応物です。これは、プロセスが信号を受信したときに取るアクションを指定するために使用されます。`sa`が`SigAction`のインスタンスであると仮定すると、そのフィールドは次のとおりです。

```julia
sa.handler         # シグナルハンドラのアドレス
sa.mask            # ブロックするシグナルのマスク
sa.flags           # ビットフラグ
```

ここで、`sa.handler`は信号を受信したときに呼び出されるC関数のアドレス（`SIG_IGN`または`SIG_DFL`である可能性があります）です。この関数は`cfunction`によって指定される場合があります。`IPC.SA_INFO`が`sa.flags`に設定されていない場合、ハンドラのシグネチャは次のようになります。

```julia
function handler(signum::Cint)::Nothing
```

これは、`Cint`型の単一の引数を取り、何も返さない関数です。`IPC.SA_INFO`が`sa.flags`に設定されている場合、ハンドラのシグネチャは次のようになります。

```julia
function handler(signum::Cint, siginf::Ptr{SigInfo}, unused::Ptr{Cvoid})::Nothing
```

これは、`Cint`、`Ptr{SigInfo}`、`Ptr{Cvoid}`の3つの引数を取り、何も返さない関数です。ハンドラによる`siginf`引数の説明については、[`SigInfo`](@ref)を参照してください。

呼び出し：

```julia
sa = SigAction()
```

新しい空の構造体を作成するか、

```julia
sa = SigAction(handler, mask, flags)
```

すべてのフィールドを提供します。

他に[`SigInfo`](@ref)、[`sigaction`](@ref)、および[`sigaction!`](@ref)も参照してください。
