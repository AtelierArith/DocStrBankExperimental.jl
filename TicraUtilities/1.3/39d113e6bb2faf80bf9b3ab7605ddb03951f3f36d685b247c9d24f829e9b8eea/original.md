```
tepp2s(tep::TEPperiodic, d; title="")
```

Convert a periodic unit cell TEP object (of type `TEPperiodic`) to a scattering surface TEP object (of type `TEPscatter`), or to a vector of such objects if `tep` contains more than a single frequency.

`d` is the is the distance between the front and rear reference planes, a `Unitful` length quantity.  The `title` keyword argument is used for the `title` field of the output object. If it is left at its default empty value, then it will be  replaced by `"TEPscatter object created by tepp2s"`.

## Usage Example

```
using Unitful: @u_str
d = 2.3u"mm"
tep_scatter = tepp2s(tep_periodic, d)
```

# Extended help

Input argument `d` is required because `TEPperiodic` uses phase reference planes located at the actual front and rear  surfaces of the unit cell, while `TEPscatter` uses the front surface only as the phase reference plane for both front and rear incidence.  Thus `d` is required to compute the necessary phase correction for rear surface incidence reflection and  for both front and rear surface incidence transmission.  This phase correction is in addition to sign changes needed for  some of the coefficients.
