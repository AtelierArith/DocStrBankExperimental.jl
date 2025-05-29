```
        n_zr = 1
    ρ1 = 1.6, α1 = 0.025, cb = 1900.0, ρb = 2.0, αb = 0.25, type = "1layer_constant")
```

Helper function to build an underwater environment for use with creating an Env object.

Optional keywords:

  * `hw`: water depth (default: 71)
  * `cw`: water sound speed (default: 1471)
  * `ρw`: water density (default: 1)
  * `αw`: water attenuation (default: 0)
  * `h1`: sediment depth (default: 10)
  * `c1`: sediment sound speed (default: 1500)
  * `ρ1`: sediment density (default: 1.6)
  * `α1`: sediment attenuation (default: 0.025)
  * `cb`: bottom sound speed (default: 1900)
  * `ρb`: bottom density (default: 2)
  * `αb`: bottom attenuation (default: 0.25)
  * `type`: type of environment to build (default: "1layer_constant")

      * "1layer_constant": 1 layer, constant sound speed
