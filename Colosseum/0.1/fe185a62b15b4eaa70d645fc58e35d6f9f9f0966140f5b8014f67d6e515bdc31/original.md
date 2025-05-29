Allows the client to execute a command in Unreal's native console, via an API. Affords access to the countless built-in commands such as "stat unit", "stat fps", "open [map]", adjust any config settings, etc. etc. Allows the user to create bespoke APIs very easily, by adding a custom event to the level blueprint, and then calling the console command "ce MyEventName [args]". No recompilation of AirSim needed!

Args:     command ([string]) Desired Unreal Engine Console command to run

Returns:     [bool]: Success
