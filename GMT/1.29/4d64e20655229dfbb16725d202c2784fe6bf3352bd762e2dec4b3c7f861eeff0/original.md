```
I = imreconstruct(marker::Union{Matrix{Bool}, Matrix{UInt8}}, Imask::GMTimage{<:UInt8, 2}; conn=4, insitu=true)
```

Perform morphological reconstruction of the image `marker` under the image `mask`.

The elements of `marker` must be less than or equal to the corresponding elements of `mask`. If the values in `marker` are greater than corresponding elements in `mask`, then $imreconstruct$ clips the values to the mask level before starting the procedure. The worphological work is done by the Leptonica function $pixSeedfillGray$.

### Args

  * `marker`: The image to be reconstructed (will hold the reconstructed image). This can be a matrix or a $GMTimage$ with Boolean or UInt8 types
  * `mask`: The mask image. Types ($GMTimage$ or matrix) are Boolean or UInt8.

### Kwargs

  * `conn::Int`: Connectivity for the image reconstruction (4 or 8). Default is 4.
  * `insitu::Bool`: If true, the input images are treated as in situ. Default is true.

### Returns

  * A new $GMTimage$ (or Matrix).

### Examlple

Use reconstruction to segment an image

```julia
text(["Hello World"], region=(1.92,2.08,1.97,2.02), x=2.0, y=2.0, font=(30, "Helvetica-Bold", :white),
     frame=(axes=:none, bg=:black), figsize=(6,0), name="tmp.png")
I = gmtread("tmp.png", band=1);
marker = fill(UInt8(0),(size(I)));
marker[390,130] = UInt8(255);
im = imreconstruct(Im, I)
```
