```
gif_animation_m3(TL_perm::AbstractMatrix, TL_induced::AbstractMatrix, TL_eddy::AbstractMatrix,
                 TL_aircraft::AbstractMatrix, B_unit::AbstractMatrix, y_nn::AbstractMatrix,
                 y::Vector, y_hat::Vector, xyz::XYZ,
                 filt_lat::Vector = [],
                 filt_lon::Vector = [];
                 ind              = trues(xyz.traj.N),
                 tt_lim::Tuple    = (0, (xyz.traj(ind).N-1)*xyz.traj.dt/60),
                 skip_every::Int  = 5,
                 save_plot::Bool  = false,
                 mag_gif::String  = "comp_xai.gif")
```

Create a GIF animation of the model 3 components and the true and predicted scalar magnetic field. First run `comp_m3_test()` to generate the individual model components 3.

**Arguments**

  * `TL_perm`:     `3` x `N` matrix of TL permanent vector field
  * `TL_induced`:  `3` x `N` matrix of TL induced vector field
  * `TL_eddy`:     `3` x `N` matrix of TL eddy current vector field
  * `TL_aircraft`: `3` x `N` matrix of TL aircraft vector field
  * `B_unit`:      `3` x `N` matrix of normalized vector magnetometer measurements
  * `y_nn`:        `3` x `N` matrix of vector neural network correction (for scalar models, in direction of `Bt`)
  * `y`:           length-`N` target vector
  * `y_hat`:       length-`N` prediction vector
  * `xyz`:         `XYZ` flight data struct
  * `filt_lat`:    (optional) length-`N` filter output latitude  [rad]
  * `filt_lon`:    (optional) length-`N` filter output longitude [rad]
  * `ind`:         (optional) selected data indices
  * `tt_lim`:      (optional) length-`2` start & end time limits (inclusive) [min]
  * `skip_every`:  (optional) number of time steps to skip between frames
  * `save_plot`:   (optional) if true, save `g1` as `mag_gif`
  * `mag_gif`:     (optional) path/name of magnetic field GIF file to save (`.gif` extension optional)

**Returns**

  * `g1`: magnetic field GIF animation

**Example**

```julia
gif_animation_m3(TL_perm, TL_induced, TL_eddy, TL_aircraft, B_unit,
                 y_nn, y, y_hat, xyz, filt_lat, filt_lon; ind=ind, tt_lim=(0.0,10.0),
                 skip_every=5, save_plot=false, mag_gif="comp_xai.gif")
```
