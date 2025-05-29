```
parse_msg!(s::NMEAData, line::AbstractString)
```

Parse a line of NMEA 0183 data and update the state of an NMEAData object.

# Arguments

s : NMEAData 	An object that stores the parsed data from NMEA messages. line : AbstractString 	A string that contains a valid NMEA 0183 message.

# Returns

DataType 	The type of the parsed message, or Nothing if the message is not supported.

# Errors

ArgumentError 	If the line is not a valid NMEA 0183 message.

# Example

```
s = NMEAData()

julia> d = [ "$GPRMC,154925.820,A,5209.732,N,00600.240,E,001.9,059.8,040123,000.0,W*7E",
			"$GPGGA,154925.920,5209.732,N,00600.240,E,1,12,1.0,0.0,M,0.0,M,,*63",
			"$GPGSA,A,3,01,02,03,04,05,06,07,08,09,10,11,12,1.0,1.0,1.0*30",
			"$GPRMC,154925.920,A,5209.732,N,00600.240,E,001.9,059.8,040123,000.0,W*7F"]
4-element Vector{String}:
 "$GPRMC,154925.820,A,5209.732,N,00600.240,E,001.9,059.8,040123,000.0,W*7E"
 "$GPGGA,154925.920,5209.732,N,00600.240,E,1,12,1.0,0.0,M,0.0,M,,*63"
 "$GPGSA,A,3,01,02,03,04,05,06,07,08,09,10,11,12,1.0,1.0,1.0*30"
 "$GPRMC,154925.920,A,5209.732,N,00600.240,E,001.9,059.8,040123,000.0,W*7F"

 julia> for str in d
			msg_type = parse_msg!(s, str)
			println(msg_type)
		end
 RMC
 GGA
 GSA
 RMC

 julia> s.last_RMC
 RMC("GPS", 56965.92, true, 52.1622, 6.004, 1.9, 59.8, "04", "01", "23", -0.0, 'A', true)

 julia> s.last_GGA
 GGA("GPS", 56965.92, 52.1622, 6.004, "GPS (SPS)", 12, 1.0, 0.0, 0.0, 0.0, 0, true)
```
