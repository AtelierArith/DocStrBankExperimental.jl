Initialize a bridge for the first time, supplying a devicetype (app name). Registering this script with the bridge may require you to run to the bridge and press the button.

The returned username is stored in the bridge.username. This is needed for future use, so you should remember it.

Returns true or false.

For example:

```
B = PhilipsHueBridge("192.168.1.2")
initialize(bridge::PhilipsHueBridge; devicetype="juliascript#user1")
testlights(B)

# B.username is something like "2e4bdae26d734a73aeec4c21d4fd6"
```

then in a future Julia session you can do:

```
B = PhilipsHueBridge("192.168.1.2", "2e4bdae26d734a73aeec4c21d4fd6")
testlights(B)
```
