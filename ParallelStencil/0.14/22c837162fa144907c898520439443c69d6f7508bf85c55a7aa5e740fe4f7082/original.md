```
@hide_communication boundary_width block
```

!!! note "Advanced"
    ```
    @hide_communication boundary_width block computation_calls=...
    @hide_communication ranges_outer ranges_inner block
    @hide_communication ranges_outer ranges_inner block computation_calls=...
    ```


Hide the communication behind the computation within the code `block`.

# Arguments

  * `boundary_width::Tuple{Integer,Integer,Integer} | Tuple{Integer,Integer} | Tuple{Integer}`: width of the boundaries in each dimension. The boundaries must include (at least) all the data that is accessed in the communcation performed.
  * `block`: code block wich starts with one [`@parallel`](@ref) call to perform computations (for exceptions, see keyword `computation_calls`), followed by code to set boundary conditions and to perform communication (as e.g. `update_halo!` from the package `ImplicitGlobalGrid`). The [`@parallel`](@ref) call to perform computations can normally not contain any positional arguments (ranges, nblocks or nthreads) nor the stream keyword argument (stream=...) (for exceptions, see keyword `computation_calls`). The code to set boundary conditions and to perform communication must only access the elements in the boundary ranges of the fields modified in the [`@parallel`](@ref) call; all elements can be acccessed from other fields. Moreover, this code must not include statements in array broadcasting notation, because they are always run on the default stream in CUDA (for CUDA.jl < v2.0), which makes CUDA stream overlapping impossible. Instead, boundary region elements can, e.g., be accessed with [`@parallel`](@ref) calls passing a ranges argument that ensures that no threads mapping to elements outside of the boundary regions are launched. Note that these [`@parallel`](@ref) `ranges` calls cannot contain any other positional arguments (nblocks or nthreads) nor the stream keyword argument (stream=...).

!!! note "Advanced"
      * `ranges_outer::`Tuple with one or multiple `ranges` as required by the corresponding argument of [`@parallel`](@ref): the `ranges` must together span (at least) all the data that is accessed in the communcation and boundary conditions performed.
      * `ranges_inner::`Tuple with one or multiple `ranges` as required by the corresponding argument of [`@parallel`](@ref): the `ranges` must together span the data that is not included by `ranges_outer`.


!!! note "Advanced keyword arguments"
      * `computation_calls=1::`number of [`@parallel`](@ref) calls at the start of the code `block` that contain the computation to be hidden behind communication. Only set this argument if you are sure that it is safe to deviate from the standard behavior (`computation_calls=1`). Note that, in many scenarios (slightly) wrong results will be obtained when `computation_calls` in greater than `1`; it is only safe, generally speaking, if no point in the boundary region computations depends on any inner point computation (finite difference derivatives can, for example, constitute such a dependency leading to wrong results).


# Examples

```
@hide_communication (16, 2, 2) begin
    @parallel diffusion3D_step!(Te2, Te, Ci, lam, dt, dx, dy, dz);
    update_halo!(Te2);
end

@hide_communication (16, 2) begin
    @parallel diffusion2D_step!(Te2, Te, Ci, lam, dt, dx, dy);
    update_halo!(Te2);
end

@hide_communication ranges_outer ranges_inner begin
    @parallel diffusion3D_step!(Te2, Te, Ci, lam, dt, dx, dy, dz);
    update_halo!(Te2);
end

@parallel_indices (iy,iz) function bc_x(A)
    A[  1, iy,  iz] = A[    2,   iy,   iz]
    A[end, iy,  iz] = A[end-1,   iy,   iz]
    return
end
@parallel_indices (ix,iz) function bc_y(A)
    A[ ix,  1,  iz] = A[   ix,    2,   iz]
    A[ ix,end,  iz] = A[   ix,end-1,   iz]
    return
end
@parallel_indices (ix,iy) function bc_z(A)
    A[ ix,  iy,  1] = A[   ix,   iy,    2]
    A[ ix,  iy,end] = A[   ix,   iy,end-1]
    return
end
@hide_communication (16, 2, 2) begin
    @parallel diffusion3D_step!(Te2, Te, Ci, lam, dt, dx, dy, dz);
    @parallel (1:size(Te,2), 1:size(Te,3)) bc_x(Te);
    @parallel (1:size(Te,1), 1:size(Te,3)) bc_y(Te);
    @parallel (1:size(Te,1), 1:size(Te,2)) bc_z(Te);
    update_halo!(Te2);
end

@hide_communication (16, 2, 2) begin
    @parallel (1:size(Te,1), 1:size(Te,2), 1:size(Te,3)) diffusion3D_step!(Te2, Te, Ci, lam, dt, dx, dy, dz);
    @parallel (1:size(Te,2), 1:size(Te,3)) bc_x(Te);
    @parallel (1:size(Te,1), 1:size(Te,3)) bc_y(Te);
    @parallel (1:size(Te,1), 1:size(Te,2)) bc_z(Te);
    update_halo!(Te2);
end

@hide_communication (16, 2, 2) computation_calls=2 begin
    @parallel computation1!(A2, A, B);
    @parallel computation2!(B, C);
    @parallel (1:size(A,2), 1:size(A,3)) bc_x(A);
    @parallel (1:size(A,1), 1:size(A,3)) bc_y(A);
    @parallel (1:size(A,1), 1:size(A,2)) bc_z(A);
    update_halo!(Te2);
end
```

!!! note "Developers note"
    The communcation should not perform any blocking operations to enable a maximal overlap of communication with computation.


See also: [`@parallel`](@ref)
