```Julia
load_xclbin!(xclbin::XRT.Xclbin; device, force) -> XRT.UUID
load_xclbin!(path::String; device, force) -> XRT.UUID

```

現在アクティブなデバイスに[`XRT.Xclbin`](@ref)オブジェクトがまだロードされていない場合、それをロードします。この関数はxclbinのUUIDを返します。`XRT.program!`は`load_xclbin!`のエイリアスです。

**キーワード**

**`device`** 対象デバイスは、`device`キーワードパラメータを設定することで変更できます。

**`force`** Xclbinをデバイスに強制的にロードします。
