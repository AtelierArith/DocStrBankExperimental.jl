`NormalizeToUnity` は、各シェルの中で最も強い線が 1.0 になるように強度を正規化します。

例:      weight(NormalizeToUnity, n"Fe L3-M5")==1.0     max(cxr=>weight(NormalizeBySubShell, cxr), characteristic(n"Fe", ltransitions))==1.0
