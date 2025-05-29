Definition for the jacobian of an analytic geometry function.

```c++
 [0,1]^\mathrm{dim} 
```

.

```c++
 \mathrm{dim} 
```

to map.

```c++
 \mathrm{dim} \cdot 3 
```

x *num_coords*. Indices

```c++
 3 \cdot i
```

,

```c++
 3 \cdot i+1 
```

,

```c++
 3 \cdot i+2 
```

correspond to the

```c++
 i 
```

-th column of the jacobian (Entry

```c++
 3 \cdot i + j 
```

is

```c++
 \frac{\partial f_j}{\partial x_i} 
```

).

# Arguments

  * `cmesh`:[in] The cmesh.
  * `gtreeid`:[in] The global tree (of the cmesh) in which the reference point is.
  * `ref_coords`:[in] Array of tree dimension x *num_coords* many entries, specifying points in
  * `num_coords`:[in] Amount of points of
  * `jacobian`:[out] The jacobian at *ref_coords*. Array of size
  * `tree_data`:[in] The data of the current tree as loaded by a t8*geom*load*tree*data_fn.
  * `user_data`:[in] The user data pointer stored in the geometry.
