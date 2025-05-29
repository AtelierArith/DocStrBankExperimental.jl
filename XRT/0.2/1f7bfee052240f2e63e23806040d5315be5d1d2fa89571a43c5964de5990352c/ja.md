```julia
Xclbin(path::AbstractString) -> XRT.Xclbin

```

`XRTWrap.Xclbin` 型で提供されるパラメータへのより便利なアクセスを可能にする構造体。ただし、必要に応じてフィールド `xclbin` で呼び出すこともできます。`Xclbin` オブジェクトのインスタンス化時に、パスやターゲットタイプなどのいくつかのチェックが行われます。

**フィールド**

**`xclbin`** は、必要に応じて `XRT.XRTWrap.Xclbin` オブジェクトへのアクセスを提供します。

**`path`** は、xclbin ファイルへの絶対パスです。

**`filename`** は、ファイル拡張子を含む xclbin ファイルのファイル名です。

**`kernels`** は、[`XRT.XclbinKernel`](@ref) 型オブジェクトのベクターを指定します。これらの要素は、メタデータに記載されたすべてのカーネルに関する情報を提供します。

**`ips`** は、[`XRT.XclbinIP`](@ref) 型オブジェクトのベクターを指定します。これらの要素は、xclbin ファイルの IP_LAYOUT セクションを表します。

**`mems`** は、[`XRT.XclbinMem`](@ref) 型オブジェクトのベクターを指定します。

**`xsa_name`** は、xclbin ファイルの Xilinx Support Archive 名です。

**`uuid`** は、xclbin ファイルの UUID です。

**`fpga_device_name`** は、メタデータに基づく FPGA デバイスの名前です。

**`target_type`** は、xlbin ファイルのタイプです。`hw`、`hw_emu`、または `sw_emu` に設定されます。

**`interface_uuid`** は、デバイスが 2RP シェルでプログラムされているときのインターフェース UUID です。XRT ≥ 2.16 のみで利用可能です。
