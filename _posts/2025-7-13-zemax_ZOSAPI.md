---
layout: single
title: "Zemax ZOSAPI on Python"
---

Zemax allows the use of its API through Python, however since a while the connection to Python stopped working as intended using modern libraries. Here I document one way of installing the latest version of Zemax 2025R1 with the python API, which can fail in a variety of ways due to using a non-supported version of Pythonnet.

## The Error

One way in which the ZOSAPI connection can break while upgrading Zemax OpticStudio is by raising an Unhandled Exception error. The error looks like this: 

```
System.IO.FileLoadException: Could not load file or assembly 'ZemaxEngine.dll' or one of its dependencies. A dynamic link library (DLL) initialization routine failed. (Exception from HRESULT:0x8007045A).```

This kind of error is not very illuminating as it can mean various things. After a clean reinstall of Zemax this error persists, which indicates there's something else going on.

## Older Python and PythonNet

Zemax is a bit cryptic on what exactly is broken with the new versions of Python and Zemax that make this incompatibility issue, however one way of fixing is by using a previous version of Python and its libraries which seems to fix the issue entirely, so here it is how I managed to fix this:

1- [Install Python 3.8](https://www.python.org/downloads/release/python-380/)
2- Install Pythonnet 2.5.2 by running: 

```pip install pythonnet==2.5.2```

This should solve these issues.