The window is detected as invalid (for example, when closed externally).

The conditions for tagging a window as invalid depend on the windowing API used. It is typically used to signal that a window crashed or does not exist, but for which an event was reported. It may however not possible to know exactly why or when a window becomes invalid. For example, the X11 protocol does not offer a way to check for window validity, since the window may get invalidated by the time the X server answer comes back. Windows that are tagged invalid should be terminated.
