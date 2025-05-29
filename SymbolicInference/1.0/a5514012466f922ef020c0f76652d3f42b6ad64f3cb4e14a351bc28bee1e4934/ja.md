persistence*barcode(time*series; range = collect(0.1:0.1:0.9), n*windows=10,alpha*thresh=0.05)

各ウィンドウのバーコードプロットを返します。 p値が `alpha_thresh` より小さい場合にポイントがプロットされます。
