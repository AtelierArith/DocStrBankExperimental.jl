```
Db = bezier(D::GMTdataset; t=nothing, np::Int=0, pure=false, firstcurve=true) -> GMTdataset
```

---

```
mat = bezier(p::Matrix{<:Real}; t=nothing, np::Int=0, pure=false, firstcurve=true) -> Matrix{Float64}
```

---

```
mat = bezier(p1::Vector{T}, p2::Vector{T}, p3::Vector{T}, p4::Vector{T}; t=nothing, np::Int=0, pure=false) where {T <: Real}
```

---

Create a Bezier curve from a set of control points.

A function for cubic Bezier interpolation for a given set of control points (knots). Each control point can exist in an N-dimensional space but only tested 2D and 3D cases. Data can be geographic or Cartesian. The default for this function is to compute a curve that passes through the control points. This can be changed by setting `pure` to `true` and then we instead compute a curve that passes through the first and last.

When more than 4 control points are provided, we make a curve composition by connecting the first curve, made with points 1,2,3,4, second curve, made with points 2,3,4,5 and so on. The way this connection is made is controlled by the `firstcurve` argument. With more than 4 control points, the `pure` option is not allowed. 

### Args

  * `D`: A $GMTdataset$ object with a matrix of control points. This matrix may have 2 (2D) or 3 columns (3D).  If `D` represents geographical data, we create a spherical Bezier curve by using an intermediate step of  converting the data to ECEF, compute the 3D curve, and then convert it back to geographic coordinates.

---

  * `p::Matrix{<:Real}`: Matrix with at least 4 control points. Same as the `D` case, except for the possibility  of geographical data.

---

  * `p1, p2, p3, p4`: Vectors of control points. They can be 2D or 3D (two or three elements).

---

### Kwargs

  * `t`: Vector of values of the $t$ paramter at which bezier curve is evaluated. By default is  evaluated at 101 evenly spaced values between 0 and 1, but see `np` below.
  * `np`: Number of values of the $t$ paramter at which bezier curve is evaluated. Default is 101.
  * `pure`: By default we compute a curve that passes through the control points. If `pure` is `true`,  we instead compute a curve that passes through the first and last control points and the other two  are used to control the path. This is what *pure* cubic bezier curves do.
  * `firstcurve`: Applies  only when the number of control points is > 4 and sets how the different  curves are connected. If `true`, the first curve takes precedence. Using as example the case of  two curves given by 5 control points; the final curve is obtained by connecting the first curve  (made with the first 4 control points) with the second curve (made with the last 4 control points).  But since these two curves shared the second, third and fourth control points, that part is removed  from the second curve, leaving only the 4rth to 5th contribution. When `firstcurve` is `false`, the  opposite happens. The first curve contributes only with the part from first to second control points.

### Returns

  * `Db`: A $GMTdataset$ object with the coordinates of the Bezier curve, when input is a $GMTdataset$.
  * `mat::Matrix{Float64}`: Matrix of coordinates of the Bezier curve, when input is a matrix.

### Example

```julia
# A spherical Bezier curve with 4 knots
D = bezier(mat2ds([30. -15; 30 45; -30 45; -30 -15], proj4="geog"));

# A composed spherical Bezier curve with 5 knots and predominance  of second curve
D = bezier(mat2ds([30. -15; 30 45; -30 45; -30 -15; -20 -25], proj4="geog"), firstcurve=false);
```
