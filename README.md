# Dandrik's Morse Trainer

Version 1.0.6

A Morse code text panel for Wolfpack multiplayer games. Sit at your U-boat's radio, type a message, and it goes out as real Morse on the radio. Morse you receive shows up as text, so you can practise sending and reading with your crew and other boats.

## Who needs it

Install it if you want to use the panel. Players without the mod still hear your Morse as tones in the game, the same as Morse keyed by hand. They just don't get the panel or the text. It works for the host and for everyone else.

## Installing

1. Close Wolfpack.
2. Install a compatible BepInEx 6 IL2CPP for Windows x64 build in the Wolfpack game folder. Builds are available from the [official BepInEx build server](https://builds.bepinex.dev/projects/bepinex_be/697/BepInEx-Unity.IL2CPP-win-x64-6.0.0-be.697%2B5362580.zip).
3. Launch the game once, then close it to create the BepInEx folders.
4. Copy your chosen mod DLLs into `Wolfpack/BepInEx/plugins/`. The repository's folder names describe who needs the mods; the DLLs all go into this same game folder.
5. Start the game. Most mods create their settings in `BepInEx/config/` on first launch. Close the game before editing those files.

To check which version you have, look in `BepInEx/LogOutput.log` after starting the game: it shows a line like `Dandrik's Morse Trainer 1.0.6 loaded.`

To update a mod, replace its old DLL rather than keeping multiple versions. If a mod has been renamed, remove the previous DLL too. To remove a mod, close the game and take its DLL out of `BepInEx/plugins/`.

## Using the panel

The panel only works while you are at the radio or the Morse key. Anywhere else it won't open.

| Key | What it does |
| --- | --- |
| F7 | Opens the panel for typing, or closes it |
| Enter | Sends the line you typed. The panel stays open for the next one |
| Enter on an empty line | Gives the keyboard back to the game, with the panel still showing. Press F7 to type again |
| Delete | Cancels the line going out and any lines waiting behind it |
| Up and Down arrows | Change the sending speed: 5, 6, 7.5, 10, 12, 15, 20 or 30 words per minute |
| Esc | Closes the panel |

- **Sending:** your line goes out exactly as you typed it, up to 75 characters. If you type another line while one is still going out, it waits its turn, up to 10 lines. Press Delete to cancel: the rest of the line isn't sent, though the last second or so already on its way still plays.
- **Leaving the radio:** the panel closes, and anything still being sent stops.
- **Underwater:** the radio has to be above water to send or receive.
- **Reading:** Morse your radio receives appears as text, labelled by sender. It reads hand keying as well as typed lines, and works out each operator's own speed and spacing, whether they use a straight key, a bug or paddles. It gets better after an operator's first line or two, because it remembers how they key.
- **New lines:** a pause of 4 seconds starts a new line, or up to 7 seconds for a slow operator.
- **A `*` in the text:** a letter the panel couldn't match to any Morse character. It is often the operator's own slip, and you'll usually see them send the word again right after.
- **What it can't fix:** uneven keying. If an operator's dots and dashes are nearly the same length, or their pauses inside a word are as long as their pauses between words, some letters will be wrong and some words will be split or run together.
- **Simplified radio missions:** these send letter by letter through the game's simplified radio. Only letters, numbers and spaces go out that way.

## Settings

Settings are in `BepInEx/config/wolfpack.dandriksmorsetrainer.cfg`, created the first time you start the game with the mod.

- `PanelKey`: the key that opens the panel. F7 by default. Pick a key that doesn't type anything, such as `F8`, `Home`, `End`, `PageUp`, `PageDown` or `Pause`, written exactly as in the list of accepted values in the file. A letter or number key would also type into the panel. `None` turns the panel off. Changes are picked up within a few seconds, even with the game running.
- `WordsPerMinute`: the sending speed. The Up and Down arrows change it too, and it is remembered.
- `WaitForClearChannel`: waits until nobody else has keyed for a few seconds before sending, so two messages don't get mixed together.

## Known issues

- Klabautermann also uses F7. If you run both mods, change `PanelKey` to another key.
- The panel may show Morse from boats on other channels as well as your own.
- If you decode with fldigi or a similar program, it may garble the first few characters of a line while it locks onto the signal.
