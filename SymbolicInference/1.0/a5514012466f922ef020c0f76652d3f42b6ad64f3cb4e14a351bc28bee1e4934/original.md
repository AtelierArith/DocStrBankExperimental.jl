persistence*barcode(time*series; range = collect(0.1:0.1:0.9), n*windows=10,alpha*thresh=0.05)

Return barcode plot for each window.      Points are plotted whenever the p-value is smaller than `alpha_thresh`.  
