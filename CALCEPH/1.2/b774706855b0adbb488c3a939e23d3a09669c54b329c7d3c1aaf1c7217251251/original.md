```
timespan(eph::Ephem)
```

This function returns the first and last time available in the ephemeris file associated to eph.

# Arguments:

  * `eph` : ephemeris

# Return:

a tuple containing:     * firsttime: Julian date of the first time     * lasttime: Julian date of the last time     * continuous: information about the availability of the quantities over the time span

```
    It returns the following value in the parameter continuous :

    1 if the quantities of all bodies are available for any time between the first and last time.
    2 if the quantities of some bodies are available on discontinuous time intervals between the first and last time.
    3 if the quantities of each body are available on a continuous time interval between the first and last time,
      but not available for any time between the first and last time.
```

See: https://www.imcce.fr/content/medias/recherche/equipes/asd/calceph/html/c/calceph.multiple.html#menu-calceph-gettimespan
