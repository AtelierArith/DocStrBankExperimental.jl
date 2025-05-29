The structure `ScanningStrategy` encodes the information needed to build a set of pointing directions. It contains the following fields:

  * `omega_spin_hz`: angular speed of the rotation around the spin axis (equal to 2πν)
  * `omega_prec_hz`: angular speed of the rotation around the precession axis (equal to 2πν)
  * `omega_year_hz`: angular speed of the rotation around the Elliptic axis (equal to 2πν)
  * `omega_hwp_hz`: angular speed of the rotation of the half-wave plate (equal to 2πν)
  * `spinsunang_rad`: angle between the spin axis and the Sun-Earth direction
  * `borespinang_rad`: angle between the boresight direction and the spin axis
  * `q1`, `q3`: quaternions used to generate the pointings

Each field has its measure unit appended to the name. For instance, field `spinsunang_rad` must be expressed in radians.
