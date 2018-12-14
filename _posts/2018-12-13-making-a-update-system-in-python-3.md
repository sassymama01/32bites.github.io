---
layout: post
title: "Making a Update System In Python 3"
author: "Noah Scott"
---

# Prolouge
Some people may wonder, why do this?

I have a simple answer to that question, usability.

Why have your users constantly checking Github for the latest release of your Python Code,

when you can write a system that checks each time the script is run.

That's what I did.

# How does it work?
So I have a ```info.json``` file in the root directory of the script.

```info.json``` has the format of this:

```json
{
    "version": "x.x.x",
    "update": "true"
}
```
What the script does is it checks for three values in the "update" key, "update", "true", and "false".

### "false"
Skip the update checks.

### "true"
Check for an update.

If there is an update available, it changes from "true" to "update".

### "update"
It know's that an update is available, and prompts for said update.

# How does it check for the update when "true"?
That's quite simple.

It uses requests to grab the remote ```info.json``` and stores it in a variable.

Then it opens the local ```info.json``` and stores it in a variable.

Then we use json to parse the version key on both variables, then store the version numbers into a variable.

Then we pass both variables into list() to convert the variables into a list.

We use the lists to grab the number from where we know where numbers are located,

and use int() to convert the numbers.

Then we compare the numbers in an if statement, and then we know whether an update is available.

# Limitations
Sadly if we use this method, the version numbers must all be one character long, aka no double digits or bigger. just single digits.
