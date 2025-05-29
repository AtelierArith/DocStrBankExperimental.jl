`SigInfo`はCの`siginfo_t`構造体を表します。これは不透明なものと見なされるべきで、その内容は`siginfo_t`のサイズに一致する符号なし整数のタプルとして保存されますが、原則として、`SA_SIGINFO`フラグで確立されたシグナルハンドラによって受け取られるべきなのはそのポインタのみです。

シグナルハンドラによって受け取られた`Ptr{SigInfo}`のインスタンス`ptr`を用いて、対応するCの`siginfo_t`構造体のメンバーは次のように取得されます：

```julia
IPC.siginfo_signo(ptr)  # シグナル番号。
IPC.siginfo_code(ptr)   # シグナルコード。
IPC.siginfo_errno(ptr)  # 非ゼロの場合、このシグナルに関連するerrno値。
IPC.siginfo_pid(ptr)    # 送信プロセスID。
IPC.siginfo_uid(ptr)    # 送信プロセスの実ユーザーID。
IPC.siginfo_addr(ptr)   # 障害が発生した命令のアドレス。
IPC.siginfo_status(ptr) # 終了値またはシグナル。
IPC.siginfo_band(ptr)   # SIGPOLLのバンドイベント。
IPC.siginfo_value(ptr)  # シグナル値。
```

これらのメソッドは*安全でない*ものであり、アドレスを直接使用するため、デフォルトではエクスポートされません。文脈によっては、`siginfo_t`のすべてのメンバーが関連するわけではなく（さらに、これらは共用体として定義されている可能性があり、したがってメモリ内で重複することがあります）、現時点ではPOSIX標準によって定義されたメンバーのみがアクセス可能です。最後に、`IPC.siginfo_value(ptr)`によって与えられる値はC型`union sigval`（Cの`int`とCの`void*`の共用体）を表し、Juliaでは両方の種類の値を表すのに十分な大きさの整数として返され（および[`sigqueue`](@ref)で設定され）ます。
