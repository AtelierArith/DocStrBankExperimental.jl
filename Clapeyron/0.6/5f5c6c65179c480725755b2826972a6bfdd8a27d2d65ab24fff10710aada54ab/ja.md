MCFlashJL(;     method = MultiComponentFlash.SSIFlash(),     storage = nothing,     V = NaN,     K = nothing,     kwargs.... )

`MultiComponentFlash.jl`の二相フラッシュソルバーを使用します。ストレージを渡してアロケーションを最小限に抑えることができます。そのストレージは、`MultiComponentFlash.flash_storage(model,p,T,z,method::MCFlashJL)`を呼び出すことで作成できます。

!!! note
    このメソッドは、現在のセッションで`MultiComponentFlash`がロードされていること（`using MultiComponentFlash`）と、julia >= v1.9が必要です。

