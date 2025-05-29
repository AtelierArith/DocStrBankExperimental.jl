/*––––––––––––––––––––––––––––––––––––––-

  * 
  * ```
                            procedure sgp4
    ```
  * 
  * this procedure is the sgp4 prediction model from space command. this is an
  * updated and combined version of sgp4 and sdp4, which were originally
  * published separately in spacetrack report #3. this version follows the
  * methodology from the aiaa paper (2006) describing the history and
  * development of the code.
  * 
  * author        : david vallado                  719-573-2600   28 jun 2005
  * 
  * inputs        :
  * tle	 - initialised structure from sgp4init() call.
  * tsince	 - time eince epoch (minutes)
  * 
  * outputs       :
  * r           - position vector                     km
  * v           - velocity                            km/sec
  * return code - non-zero on error.
  * ```
                  1 - mean elements, ecc >= 1.0 or ecc < -0.001 or a < 0.95 er
    ```
  * ```
                  2 - mean motion less than 0.0
    ```
  * ```
                  3 - pert elements, ecc < 0.0  or  ecc > 1.0
    ```
  * ```
                  4 - semi-latus rectum < 0.0
    ```
  * ```
                  5 - epoch elements are sub-orbital
    ```
  * ```
                  6 - satellite has decayed
    ```
  * 
  * locals        :
  * am          -
  * axnl, aynl        -
  * betal       -
  * cosim   , sinim   , cosomm  , sinomm  , cnod    , snod    , cos2u   ,
  * sin2u   , coseo1  , sineo1  , cosi    , sini    , cosip   , sinip   ,
  * cosisq  , cossu   , sinsu   , cosu    , sinu
  * delm        -
  * delomg      -
  * dndt        -
  * eccm        -
  * emsq        -
  * ecose       -
  * el2         -
  * eo1         -
  * eccp        -
  * esine       -
  * argpm       -
  * argpp       -
  * omgadf      -
  * pl          -
  * r           -
  * rtemsq      -
  * rdotl       -
  * rl          -
  * rvdot       -
  * rvdotl      -
  * su          -
  * t2  , t3   , t4    , tc
  * tem5, temp , temp1 , temp2  , tempa  , tempe  , templ
  * u   , ux   , uy    , uz     , vx     , vy     , vz
  * inclm       - inclination
  * mm          - mean anomaly
  * nm          - mean motion
  * nodem       - right asc of ascending node
  * xinc        -
  * xincp       -
  * xl          -
  * xlm         -
  * mp          -
  * xmdf        -
  * xmx         -
  * xmy         -
  * nodedf      -
  * xnode       -
  * nodep       -
  * np          -
  * 
  * coupling      :
  * getgravconst-
  * dpper
  * dpspace
  * 
  * references    :
  * hoots, roehrich, norad spacetrack report #3 1980
  * hoots, norad spacetrack report #6 1986
  * hoots, schumacher and glover 2004
  * vallado, crawford, hujsak, kelso  2006  ––––––––––––––––––––––––––––––––––––––*/
