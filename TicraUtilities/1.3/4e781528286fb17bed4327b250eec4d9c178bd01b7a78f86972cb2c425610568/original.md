```
teps2p(tep::TEPscatter, d, freq; name="tep_periodic", class="created_by_teps2p")
```

Convert a scattering TEP object (of type `TEPscatter`) to a periodic unit cell TEP object (of type `TEPperiodic`).

`d` is the is the distance between the front and rear reference  planes, a `Unitful` quantity. `freq` is the frequency, also a `Unitful` quantity.   `tep` and `freq` may be both scalars or both vectors of the same length.   In the latter case, each entry corresponds to a specific frequency.

## Usage Example

```
using Unitful: @u_str
freqs = [1.2u"GHz", 2u"GHz"] # Assumes teps is a vector of 2 TEPscatter objects
d = 2.3u"mm"
tep_periodic = teps2p(teps, d, freqs)
```

# Extended help

Input argument `freq` is required because the frequencies are part of the data stored in a `TEPperiodic` object, but not in a `TEPscatter` object.  Additionally, both `freq` and `d` arguments are required because `TEPperiodic` uses phase reference  planes located at the actual front and rear surfaces of the unit cell, while `TEPscatter` uses the front surface only as the phase reference plane for both front and rear incidence.  Thus, these arguments are required to compute the necessary phase correction for rear surface incidence reflection and for both front and rear surface incidence transmission.   This phase correction is in addition to sign changes needed for some of the coefficients.
