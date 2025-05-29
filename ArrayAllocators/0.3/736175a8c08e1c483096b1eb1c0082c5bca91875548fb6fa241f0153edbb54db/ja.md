```
MemAlign([alignment::Integer])
```

アラインされたメモリを割り当てます。プラットフォーム固有の実装のエイリアスです。

`alignment` は2の累乗でなければなりません。

POSIXシステムでは、`alignment` は `sizeof(Ptr)` の倍数でなければなりません。Windowsでは、`alignment` は2^16の倍数でなければなりません。

`alignment` が指定されていない場合、`min_alignment(MemAlign)` に設定されます。

`MemAlign` は次のプラットフォーム固有の実装のいずれかへの定数エイリアスです。

  * POSIX (LinuxおよびmacOS): [`POSIX.PosixMemAlign`](@ref)
  * Windows: [`Windows.WinMemAlign`](@ref).
