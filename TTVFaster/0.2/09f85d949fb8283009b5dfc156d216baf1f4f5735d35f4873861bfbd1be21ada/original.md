If nplanet=2 and we want to model that planet 2 hosts a satellite in a circular orbit:  Arguments (if different from above):   params: Holds 5 elements of each planet, plus 3 for satellite     treat*PMB*as_planet: Whether to treat the Planet-Moon Barycenter as an observed planet for p2 (i.e. for case where Earth has no Moon)

Returns:   tts:   The model transit times for the observed planets with model TTVs for the system.
