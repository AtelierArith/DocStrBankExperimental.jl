```
ITRF{Year}([epoch])
```

Construct an object representing the International Terrestrial Reference Frame for the given `Year` of realization.  ITRF is the standard high accuracy terrestrial reference frame for worldwide use.  An optional `epoch` parameter defines the time of interest - typically a date at which coordinates were measured, using, eg a GPS device.  Without the `epoch` parameter, the resulting `ITRF{Year}` object represents the full dynamic datum.

A *realization* is created every few years by computing the position of a large set of ground control stations from satellite and celestial measurements.  The `Year` parameter represents the last year from which data was used in the frame processing regression problem.  A list of recent realizations is available at http://itrf.ensg.ign.fr/ITRF_solutions; as of 2016-07 valid `Year`s were 2014 2008 2005 2000 1997 1996 1994 1993 1992 1991 1990 1989 1988.

See http://itrf.ensg.ign.fr/general.php for a technical overview.  Useful technical papers:

  * "IERS Conventions (2010)", Petit and Luzum (eds.), IERS Technical note No.36,  Chapter 4, https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html
  * "ITRF2008: an improved solution of the international terrestrial reference  frame", Altamimi et al., J. Geodesy (2011) 85: 457,  http://dx.doi.org/10.1007/s00190-011-0444-4
  * "IGS08: the IGS realization of ITRF2008", Rebischung et al., GPS Solutions  (2012) 16: 483, http://dx.doi.org/10.1007/s10291-011-0248-2,  ftp://igs.org/pub/resource/pubs/IGS08*The*IGS*Realization*of_ITRF2008.pdf
  * "The IGS contribution to ITRF2014", Rebischung et al., J. Geodesy (2016) 90:  611, http://dx.doi.org/10.1007/s00190-016-0897-6
