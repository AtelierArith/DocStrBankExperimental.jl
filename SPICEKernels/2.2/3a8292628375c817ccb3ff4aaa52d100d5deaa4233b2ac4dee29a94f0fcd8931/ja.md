```julia
fetchkernel(kernel; directory, ignorecache)

```

与えられたエフェメリスファイル名に基づいて、ファイルを`SPICEKernels.jl`のスクラッチスペースにダウンロードし、ファイルの場所へのパスを返します。完全なURLまたはパスが提供されている場合、そのパスが使用されます。それ以外の場合、`kernel`はSPICE一般カーネルであると見なされます。

# 拡張ヘルプ

`ignorecache`が有効になっている場合、エフェメリスファイルは、`SPICEKernels.jl`のスクラッチスペースに既に存在していても再ダウンロードされます。`directory`が`SPICEKernels.SPICE_KERNEL_DIR`変数以外の何かに設定されている場合、ファイルは`SPICEKernels.jl`のスクラッチスペースではなく、提供されたディレクトリにダウンロードされます。
