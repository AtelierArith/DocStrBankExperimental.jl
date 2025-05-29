```
gif_ellipse(P, lat1 = deg2rad(45);
            dt                   = 0.1,
            di::Int              = 10,
            speedup::Int         = 60,
            conf_units::Symbol   = :m,
            μ                    = zeros(eltype(P),2),
            conf                 = 0.95,
            clip                 = Inf,
            n::Int               = 61,
            lim                  = 500,
            margin::Int          = 2,
            axis::Bool           = true,
            plot_eigax::Bool     = false,
            bg_color::Symbol     = :white,
            ce_color::Symbol     = :black,
            b_e::AbstractBackend = gr(),
            save_plot::Bool      = false,
            ellipse_gif::String  = "conf_ellipse.gif")
```

Create a (position) confidence ellipse GIF animation for a `2` x `2` (x `N`) covariance matrix.

**Arguments:**

  * `P`:           `2` x `2` (x `N`) covariance matrix
  * `lat1`:        (optional) nominal latitude [rad], only used if `conf_units = :m` or `:ft`
  * `dt`:          (optional) measurement time step [s]
  * `di`:          (optional) GIF measurement interval (e.g., `di = 10` uses every 10th measurement)
  * `speedup`:     (optional) GIF speedup (e.g., `speedup = 60` is 60x speed)
  * `conf_units`:  (optional) confidence ellipse units {`:m`,`:ft`,`:deg`,`:rad`}
  * `μ`:           (optional) confidence ellipse center [`conf_units`]
  * `conf`:        (optional) percentile {0:1}
  * `clip`:        (optional) clipping radius [`conf_units`]
  * `n`:           (optional) number of confidence ellipse points
  * `lim`:         (optional) plot `x` & `y` limits (`-lim`,`lim`) [`conf_units`]
  * `margin`:      (optional) margin around plot [mm]
  * `axis`:        (optional) if true, show axes
  * `plot_eigax`:  (optional) if true, show major & minor axes
  * `bg_color`:    (optional) background color
  * `ce_color`:    (optional) confidence ellipse color
  * `b_e`:         (optional) plotting backend
  * `save_plot`:   (optional) if true, save `g1` as `ellipse_gif`
  * `ellipse_gif`: (optional) path/name of confidence ellipse GIF file to save (`.gif` extension optional)

**Returns:**

  * `g1`: confidence ellipse GIF animation
