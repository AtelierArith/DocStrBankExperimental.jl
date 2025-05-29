```
fits_resize_img(f::FITSFile, T::Type, naxis::Integer,
                sz::Union{Vector{<:Integer}, Tuple{Vararg{Integer}}})
```

Modify the size, dimensions and optionally the element type of the image in `f`. The new image will have an element type `T`, be a `naxis`-dimensional image with size `sz`. If the new image is larger than the existing one, it will be zero-padded at the end. If the new image is smaller, existing image data will be truncated.

!!! note
    This method reinterprets the data instead of coercing the elements.


# Example

```jldoctest
julia> f = fits_clobber_file(tempname());

julia> a = [1 2; 3 4];

julia> fits_create_img(f, a);

julia> fits_write_pix(f, a);

julia> fits_get_img_size(f)
2-element Vector{Int64}:
 2
 2

julia> fits_resize_img(f, [3,3]);

julia> fits_get_img_size(f)
2-element Vector{Int64}:
 3
 3

julia> b = similar(a, (3,3));

julia> fits_read_pix(f, b); b
3×3 Matrix{Int64}:
 1  4  0
 3  0  0
 2  0  0

julia> fits_resize_img(f, [4]);

julia> b = similar(a, (4,));

julia> fits_read_pix(f, b); b
4-element Vector{Int64}:
 1
 3
 2
 4
```
