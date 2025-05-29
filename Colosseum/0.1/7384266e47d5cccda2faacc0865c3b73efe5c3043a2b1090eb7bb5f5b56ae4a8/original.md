Prints the specified message in the simulator's window.

If message*param is supplied, then it's printed next to the message and in that case if this API is called with same message value but different message*param again then previous line is overwritten with new line (instead of API creating new line on display).

For example, `simPrintLogMessage("Iteration: ", to_string(i))` keeps updating same line on display when API is called with different values of i. The valid values of severity parameter is 0 to 3 inclusive that corresponds to different colors.

Args:     message (str) Message to be printed     message_param (str, optional) Parameter to be printed next to the message     severity (int, optional) Range 0-3, inclusive, corresponding to the severity of the message
