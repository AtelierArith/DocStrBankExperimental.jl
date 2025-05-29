Compute new GMPE PGA/intensity grid using weighted averaging method

**IN**

  * `config` configuration of weighted averaging procedure
  * `grid` GMPE field modeling by any of `gmpe_*` method
  * `intensity_measures` Intensity measures by felt reports or stations
  * `intensity_in_pga` is the intensity measures in PGA %g.gg units? Otherwise intensity in SSI is assumes.
  * `pga_out` if set to `true` function will return corrected GMPE filed in %g.gg units

**OUT** Corrected GMPE field in `Array{Point_pga_out}` or `Array{Point_ssi_out}`
