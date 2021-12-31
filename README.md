<p align="center"><img src="https://github-readme-stats.vercel.app/api?username=xzripper&&show_icons=true&theme=radical"></p>
<p align="center"><img src="https://github-readme-stats.vercel.app/api/top-langs/?username=xzripper&langs_count=6"></p>
<br>
<h1>🌈 Hello, my name is Ivan! And i 💖 code! 🌈</h1>
<h2>I am not working.</h2>
<h3>Here my languages.
<br>
🐍 Python 🐍,
<br>
📜 Lua 📜,
<br>
🔵 Golang 🔵,
<br>
☕ Java ☕.
<br>
</h3>
<h4>My <a href='https://t.me/dieeid/'>Telegram</a>.</h4>
<h5>Languages i know.
<br>
🟡 Ukraine 🟡,
<br>
⚪ Russian ⚪,
<br>
🔴 English 🔴,
<br>
🟢 Belarusian 🟢
<br>
</h5>
<p>Languages using percent.</p>
<ul>
  <li>Python - 40%,</li>
  <li>Lua - 20%,</li>
  <li>Golang - 10%,</li>
  <li>Java - 30%.</li>
</ul>
<h1>Some source code!</h1>
<p>Here some source code, which on my mind the best in my repositories!</p>

<h3>Python!</h3>
<b><a href="https://github.com/xzripper/LanguageCreator/blob/main/langcreator/stringparser.py">stringparser.py</a></b>
<br>
<br>

```python
from typing import Union


class StringParser:
    def __init__(self, string: str) -> None:
        """
        String parser tools.
        If string is not str, string will be None.
        :param string: String to parse.
        """
        if type(string) is not str:
            self.string = None

        elif type(string) is str:
            self.string = string

    def getstr(self) -> Union[None, str]:
        """Get user string."""
        return self.string

    def updatestr(self, string: str) -> None:
        """
        Replace old string on new string.
        :param string: Updated string.
        """
        self.__init__(string)

    def cutstart(self, fr: int) -> Union[None, str]:
        """
        Cut string from start.
        :param fr: Cut from.
        """
        if self.string is None:
            return self.string

        return self.string[fr:]

    def cutend(self, fr: int) -> Union[None, str]:
        """
        Cut string from end.
        :param fr: Cut from.
        """
        if self.string is None:
            return self.string

        return self.string[:fr]

    def cut(self, start: int, end: int) -> Union[None, str]:
        """
        Cut string by start and end.
        :param start: Cut from start.
        :param end: Cut from end.
        """
        if self.string is None:
            return self.string

        return self.string[start:][:end]

    def remspaces(self, side: str) -> Union[None, str]:
        """
        Remove spaces from n side.
        Returns None if error.
        :param side: Remove spaces from n side.
        """
        if self.string is None:
            return self.string

        if side == 'right':
            return self.string.rstrip()

        elif side == 'left':
            return self.string.lstrip()

        elif side == 'all':
            return self.string.rstrip().lstrip()

        else:
            return None

    def replace(self, old: Union[tuple, list, str], new: Union[tuple, list, str]) -> Union[None, str]:
        """
        Replace old character on new.
        If old and new is tuple or list, it's removes old characters on new characters.
        :param old: Old character.
        :param new: New character.
        """
        if self.string is None:
            return self.string

        replaced = self.string

        if (type(old) is tuple or type(old) is list) and (type(new) is tuple or type(new) is list):
            if len(new) < len(old) or len(new) > len(old):
                return None

            for i in range(len(old)):
                replaced = replaced.replace(old[i], new[i])

            return replaced

        elif (type(old) is str) and (type(new) is str):
            return self.string.replace(old, new)

        else:
            return None

    def crash(self, separator: Union[tuple, list, str], getdict: bool = False) -> Union[None, list, dict]:
        """
        Crash a string by separator.
        If separator is tuple or list, it will be splitting step by step.
        If separator is not str or tuple or list, returns None.
        :param separator: Separator to crash.
        :param getdict: Get dict as return when separator is tuple or list.
        """
        if self.string is None:
            return self.string

        dsplitted = {}
        splitted = []

        if type(separator) is tuple or type(separator) is list:
            if getdict:
                for divider in separator:
                    dsplitted[divider] = self.string.split(divider)

                return dsplitted

            elif not getdict:
                for divider in separator:
                    splitted.append(self.string.split(divider))

                return splitted

        elif type(separator) is str:
            return self.string.split(separator)

        else:
            return None

    def remove(self, char: str, times: int) -> Union[None, str]:
        """
        Remove character from string.
        If times is -1, removing all, else removing only N times.
        :param char: Character to remove.
        :param times: Remove character N times.
        """
        if self.string is None:
            return self.string

        if times == -1:
            return self.string.replace(char, '')

        elif times != -1:
            return self.string.replace(char, '', times)

    def tocase(self, case: int) -> Union[None, str]:
        """
        Convert string to case.
        Types:
            1 - To lower.
            2 - To upper.
            3 - To title.
            4 - Capitalize.
        :param case: Type of case.
        """
        if self.string is None:
            return self.string

        if case == 1:
            return self.string.lower()

        elif case == 2:
            return self.string.upper()

        elif case == 3:
            return self.string.title()

        elif case == 4:
            return self.string.capitalize()

        else:
            return None

    def inscobes(self, rlcs: bool) -> Union[None, bool]:
        """
        Is string in scobes.
        If rlcs is not True and not False, returns None.
        :param rlcs: Is "<>" scobes too.
        """
        if self.string is None:
            return self.string

        scobes = f'{self.string[0]}{self.string[-1]}'

        if rlcs:
            return scobes == '()' or scobes == '[]' or scobes == '{}' or scobes == '<>'

        elif not rlcs:
            return scobes == '()' or scobes == '[]' or scobes == '{}'

        else:
            return None

    def getfromscobes(self) -> Union[None, str]:
        """
        Get string from scobes.
        If string not in scobes, returns None.
        """
        if self.string is None:
            return self.string

        if not self.inscobes(True):
            return None

        elif self.inscobes(True):
            return self.cut(1, -1)

    def instring(self, string: str) -> Union[None, bool]:
        """
        Is sub-string in string.
        :param string: Sub-string.
        """
        if self.string is None:
            return None

        return string in self.string

    @staticmethod
    def newstr(string: str) -> str:
        """
        Get user object from args converted in str.
        :param string: Target string.
        """
        return str(string)

    def clearstr(self) -> None:
        """Clear string."""
        self.string = None
```

<h4>Lua!</h4>
<b><a href="https://github.com/xzripper/LuaUI/blob/main/LuaUI.lua">LuaUI.lua</a></b>
<br>
<br>

```lua
--[[
    Simple GUI Libray for Lua,
    based on tkinter.
    Wrapper for Tkinter, on Lua.
    Converts Lua code to Python.
    What you need to know, to programm UI on Lua:
        Basic`s of Lua,
        Basic`s of Python,
        Basic`s of Tkinter, (Optionally).
    Languages: Python, Lua.
    Author: Ivan Perzhinsky.
    Version: 1.0
--]]

libraryName = "LuaUI" -- Library name.
libraryAuthor = "Ivan Perzhinsky" -- Author of library.
libraryVersion = 1.0 -- Version of library.

UI = {} -- UI Class.
UIWidgets = {} -- Widgets.
UIWidgetsMethods = {} -- Widgets method. Like get text, is RB checked.

UI.windowName = nil -- Window name.
UI.defaultWindowIcon = "default.ico" -- Default window icon.
UI.atExitCode = nil -- Exit code default.
UI.undefined = nil -- Undefined.

UIWidgets.windowWidgets = {} -- Widgets in window.

MINIMAL_MEMORY = 0x1 -- Minimal memory for library.

-- Default functions of UI.

-- Create new window.
---@param windowName? string
function UI.newWindow(windowName)
    UI.windowName = windowName

    local newWindowInstance = io.open(windowName..".py", "w") -- Creating new window instance.
    newWindowInstance:write("# Window generated by LuaUI.lua.\n# Please do not touch the window, if you dont know what you do.\n# Change the code only for bug or error deciding.\n# By LuaUI.\n\nfrom tkinter import *\nfrom tkinter import messagebox\nfrom tkinter.ttk import Radiobutton, Checkbutton, Combobox\nfrom time import sleep\nfrom sys import exit as kill\n\n\nwindow = Tk()\n")
    newWindowInstance:close() -- Close window instance.
end

-- Set window title.
---@param windowName? string
---@param windowTitle? string
function UI.setTitle(windowName, windowTitle)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.
    windowInstance:write("window.title('"..windowTitle.."')\n")
    windowInstance:close() -- Close window instance.
end

-- Set window geometry.
---@param windowName? string
---@param x? integer
---@param y? integer
function UI.setGeometry(windowName, x, y)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.
    windowInstance:write("window.geometry('"..tostring(x).."x"..tostring(y).."')\n")
    windowInstance:close() -- Close window instance.
end

-- Set window resizable.
---@param windowName? string
---@param isResizable? boolean
function UI.setResizable(windowName, isResizable)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.

    if isResizable then -- Set resizable.
        windowInstance:write("window.resizable(True, True)\n")

    elseif not isResizable then -- Set resizable to false.
        windowInstance:write("window.resizable(False, False)\n")
    end

    windowInstance:close() -- Close window instance.
end

-- Set window icon.
---@param windowName? string
---@param windowIcon? string
function UI.setWindowIcon(windowName, windowIcon)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.
    windowInstance:write("window.iconbitmap('"..windowIcon.."')\n")
    windowInstance:close() -- Close window instance.
end

-- Run app.
---@param windowName? string
function UI.runWindow(windowName)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.
    windowInstance:write("window.mainloop()\n")
    windowInstance:close() -- Close window instance.

    os.execute("python "..windowName..".py") -- Executing app.

    if UI.atExitCode ~= UI.undefined then
        UI.atExitCode()
    end
end

-- Do work at end of app.
---@param code? string
function UI.doWorkAtExit(code)
    UI.atExitCode = code
end

-- Is element is list.
---@param element? any
---@param list? table
function isElementInList(element, list)
    function isElementInList(element, list)
        local indexList = 0x1
        local listLenght = #list
    
        for listElement = indexList, listLenght do
            if list[listElement] == element then
                return true
            end
        end

        return false
    end
end

-- Widgets of UI.

-- Label.
---@param windowName? string
---@param labelName? string
---@param labelText? string
---@param fontName? string
---@param fontSize? integer
---@param column? integer
---@param row? integer
---@param x? integer
---@param y? integer
function UIWidgets.newLabel(windowName, labelName, labelText, fontName, fontSize, column, row, x, y)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.

    if isElementInList(labelName, UIWidgets.windowWidgets) then -- If widget name exists in window.
        error("Widget with this name is alredy exists.", 3)

    else -- If widget name not exists in window.
        table.insert(UIWidgets.windowWidgets, labelName) -- Inserting widget name.
        windowInstance:write(labelName.." = Label(window, text='"..labelText.."', font=('"..fontName.."', "..tostring(fontSize).."))\n"..labelName..".grid(column="..tostring(column)..", row="..tostring(row)..", padx="..tostring(x)..", pady="..tostring(y)..")\n")
    end

    windowInstance:close() -- Close window instance.
end

-- Button.
---@param windowName? string
---@param buttonName? string
---@param buttonText? string
---@param fontName? string
---@param fontSize? integer
---@param column? integer
---@param row? integer
---@param x? integer
---@param y? integer
---@param onclick? string
function UIWidgets.newButton(windowName, buttonName, buttonText, fontName, fontSize, column, row, x, y, onclick)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.

    if isElementInList(buttonName, UIWidgets.windowWidgets) then -- If widget name exists in window.
        error("Widget with this name is alredy exists.", 3)

    else -- If widget name not exists in window.
        table.insert(UIWidgets.windowWidgets, buttonName) -- Inserting widget name.
        windowInstance:write(buttonName.." = Button(window, text='"..buttonText.."', font=('"..fontName.."', "..tostring(fontSize).."), command=lambda: exec('"..onclick.."'))\n"..buttonName..".grid(column="..tostring(column)..", row="..tostring(row)..", padx="..tostring(x)..", pady="..tostring(y)..")\n")
    end

    windowInstance:close() -- Close window instance.
end

-- Entry.
---@param windowName? string
---@param entryName? string
---@param width? integer
---@param column? integer
---@param row? integer
---@param x? integer
---@param y? integer
function UIWidgets.newEntry(windowName, entryName, width, column, row, x, y)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.

    if isElementInList(entryName, UIWidgets.windowWidgets) then -- If widget name exists in window.
        error("Widget with this name is alredy exists.", 3)

    else
        table.insert(UIWidgets.windowWidgets, entryName) -- Inserting widget name.
        windowInstance:write(entryName.." = Entry(window, width="..tostring(width)..")\n"..entryName..".grid(column="..tostring(column)..", row="..tostring(row)..", padx="..tostring(x)..", pady="..tostring(y)..")\n")
    end

    windowInstance:close() -- Close window instance.
end

-- Checkbutton.
---@param windowName? string
---@param checkButtonName? string
---@param text? string
---@param column? integer
---@param row? integer
---@param x? integer
---@param y? integer
function UIWidgets.newCheckButton(windowName, checkButtonName, text, column, row, x, y)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.

    if isElementInList(checkButtonName, UIWidgets.windowWidgets) then -- If widget name exists in window.
        error("Widget with this name is alredy exists.", 3)

    else
        table.insert(UIWidgets.windowWidgets, checkButtonName) -- Inserting widget name.
        windowInstance:write(checkButtonName.." = Checkbutton(window, text='"..text.."')\n"..checkButtonName..".grid(column="..tostring(column)..", row="..tostring(row)..", padx="..tostring(x)..", pady="..tostring(y)..")\n")
    end

    windowInstance:close() -- Close window instance.
end


-- Radiobutton.
---@param windowName? string
---@param radioButtonName? string
---@param text? string
---@param column? integer
---@param row? integer
---@param x? integer
---@param y? integer
function UIWidgets.newRadioButton(windowName, radioButtonName, text, column, row, x, y)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.

    if isElementInList(radioButtonName, UIWidgets.windowWidgets) then -- If widget name exists in window.
        error("Widget with this name is alredy exists.", 3)

    else
        table.insert(UIWidgets.windowWidgets, radioButtonName) -- Inserting widget name.
        windowInstance:write(radioButtonName.." = Radiobutton(window, text='"..text.."')\n"..radioButtonName..".grid(column="..tostring(column)..", row="..tostring(row)..", padx="..tostring(x)..", pady="..tostring(y)..")\n")
    end

    windowInstance:close() -- Close window instance.
end

-- Plain text.
---@param windowName? string
---@param plainTextName? string
---@param width? string
---@param height? string
---@param column? integer
---@param row? integer
---@param x? integer
---@param y? integer
function UIWidgets.newPlainText(windowName, plainTextName, width, height, column, row, x, y)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.

    if isElementInList(plainTextName, UIWidgets.windowWidgets) then -- If widget name exists in window.
        error("Widget with this name is alredy exists.", 3)

    else
        table.insert(UIWidgets.windowWidgets, plainTextName) -- Inserting widget name.
        windowInstance:write(plainTextName.." = Text(window, width="..tostring(width)..", height="..tostring(height)..")\n"..plainTextName..".grid(column="..tostring(column)..", row="..tostring(row)..", padx="..tostring(x)..", pady="..tostring(y)..")\n")
    end

    windowInstance:close() -- Close window instance.
end

-- Combo box.
---@param windowName? string
---@param comboBoxName? string
---@param data? table
---@param current? any
---@param column? integer
---@param row? integer
---@param x? integer
---@param y? integer
function UIWidgets.newComboBox(windowName, comboBoxName, data, current, column, row, x, y)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.

    if isElementInList(comboBoxName, UIWidgets.windowWidgets) then -- If widget exists.
        error("Widget with this name is alredy exists.", 3)

    else -- If widget not exists.
        table.insert(UIWidgets.windowWidgets, comboBoxName) -- Inserting widget name.
        windowInstance:write(comboBoxName.." = Combobox(window)\n"..comboBoxName.."['values'] = ("..table.concat(data, ',')..")\n"..comboBoxName..".current("..current..")\n"..comboBoxName..".grid(column="..tostring(column)..", row="..tostring(row)..", padx="..tostring(x)..", pady="..tostring(y)..")\n")
    end

    windowInstance:close() -- Close window instance.
end

-- Show info messagebox.
---@param windowName? string
---@param title? string
---@param mainText? string
function UIWidgets.messageInfo(windowName, title, mainText)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.
    windowInstance:write("messagebox.showinfo('"..title.."', '"..mainText.."')\n")
    windowInstance:close() -- Close window instance.
end

-- Show warning messagebox.
---@param windowName? string
---@param title? string
---@param mainText? string
function UIWidgets.messageWarning(windowName, title, mainText)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.
    windowInstance:write("messagebox.showwarning('"..title.."', '"..mainText.."')\n")
    windowInstance:close() -- Close window instance.
end

-- Show error messagebox.
---@param windowName? string
---@param title? string
---@param mainText? string
function UIWidgets.messageError(windowName, title, mainText)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.
    windowInstance:write("messagebox.showerror('"..title.."', '"..mainText.."')\n")
    windowInstance:close() -- Close window instance.
end

-- Get widgets name.
function UIWidgets.getWidgetsFromWindow()
    local indexList = 0x1
    local widgets = ""

    for widget = indexList, #UIWidgets.windowWidgets do
        if UIWidgets.windowWidgets[widget] == UIWidgets.windowWidgets[#UIWidgets.windowWidgets] then
            widgets = widgets..UIWidgets.windowWidgets[widget]

        else
            widgets = widgets..UIWidgets.windowWidgets[widget].."\n"
        end
    end

    return widgets
end

-- Stop GUI script on time.
---@param windowName? string
---@param time? integer
function UIWidgets.wait(windowName, time)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.
    windowInstance:write("sleep("..tostring(time)..")\n")
    windowInstance:close() -- Close window instance.
end


-- Methods of widgets.

-- Get text from entry.
---@param windowName? string
---@param resultName? string
---@param entryName? string
function UIWidgetsMethods.getEntryText(windowName, resultName, entryName)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.

    if isElementInList(resultName, UIWidgets.windowWidgets) then -- If widget name exists in window.
        error("Widget or variable with this name is alredy exists.", 3)

    else
        table.insert(UIWidgets.windowWidgets, resultName)
        windowInstance:write(resultName.." = "..entryName..".get()\n")
    end

    windowInstance:close() -- Close window instance.
end

-- Is Radiobutton checked.
---@param windowName? string
---@param resultName? string
---@param radioButtonName? string
function UIWidgetsMethods.getRadioButtonText(windowName, resultName, radioButtonName)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.

    if isElementInList(resultName, UIWidgets.windowWidgets) then -- If widget name exists in window.
        error("Widget or variable with this name is alredy exists.", 3)

    else
        table.insert(UIWidgets.windowWidgets, resultName)
        windowInstance:write(resultName.." = "..radioButtonName..".get()\n")
    end

    windowInstance:close() -- Close window instance.
end

-- Is Radiobutton checked.
---@param windowName? string
---@param resultName? string
---@param checkButtonName? string
function UIWidgetsMethods.isCheckButtonChecked(windowName, resultName, checkButtonName)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.

    if isElementInList(resultName, UIWidgets.windowWidgets) then -- If widget name exists in window.
        error("Widget or variable with this name is alredy exists.", 3)

    else
        table.insert(UIWidgets.windowWidgets, resultName)
        windowInstance:write(resultName.." = "..checkButtonName..".get()\n")
    end

    windowInstance:close() -- Close window instance.
end

-- Get request to widget.
---@param windowName? string
---@param resultName? string
---@param widgetName? string
function UIWidgetsMethods.get(windowName, resultName, widgetName)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.

    if isElementInList(resultName, UIWidgets.windowWidgets) then -- If widget name exists in window.
        error("Widget or variable with this name is alredy exists.", 3)

    else
        table.insert(UIWidgets.windowWidgets, resultName)
        windowInstance:write(resultName.." = "..widgetName..".get()\n")
    end

    windowInstance:close() -- Close window instance.
end

-- Set text in entry or plain text.
---@param windowName? string
---@param textName? string
---@param text? string
function UIWidgetsMethods.setText(windowName, textName, text)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.
    windowInstance:write(textName..".insert(INSERT, '"..text.."')\n")
    windowInstance:close() -- Close window instance.
end

-- Delete text in entry or plain text.
---@param windowName? string
---@param coordinates? string
---@param textName? string
function UIWidgetsMethods.deleteText(windowName, coordinates, textName)
    local windowInstance = io.open(windowName..".py", "a") -- Creating window instance.
    windowInstance:write(textName..".delete("..tostring(coordinates)..", END)\n")
    windowInstance:close() -- Close window instance.
end

-- Add user-code.
---@param windowSource? string
---@param code? string
function addCode(windowSource, code)
    local windowInstance = io.open(windowSource..".py", "a") -- Creating window instance.
    windowInstance:write(code) -- User code.
    windowInstance:close() -- Close window instance.
end

-- Stop script on time.
---@param time? integer
function wait(time)
    local clock = os.clock
    local tminus = clock()
    while clock() - tminus <= time do end
end

-- Wrapper for creating window.
---@param windowName? string
---@param windowTitle? string
---@param windowX? integer
---@param windowY? integer
---@param isResizable? boolean
---@param windowIcon? string
---@param atExitCode? string
---@param runWindow? boolean
function createWindow(windowName, windowTitle, windowX, windowY, isResizable, windowIcon, atExitCode, runWindow)
    UI.windowName = windowName -- Set window name.

    UI.newWindow(windowName) -- Create window.
    UI.setTitle(windowName, windowTitle) -- Set window title.
    UI.setGeometry(windowName, windowX, windowY) -- Set geometry.
    UI.setResizable(windowName, isResizable) -- Set resizable.
    UI.setWindowIcon(windowName, windowIcon) -- Set window icon.

    if atExitCode == UI.undefined then -- If exit code is undefined.
        UI.doWorkAtExit(UI.undefined)

    else -- If exit code is defined/
        UI.doWorkAtExit(atExitCode)
    end

    if runWindow then -- If runWindow is True.
        UI.runWindow(windowName)
    end
end

-- Import a lua library.
---@param modulename? string
function import(modulename)
    require(modulename)
end

-- Import a python library.
---@param windowName? string
---@param modulename? string
function importLibrary(windowName, modulename)
    addCode(windowName, "import "..modulename.."\n")
end

-- Execute python.
---@param pythonFile? string
function executePython(pythonFile)
    os.execute("python "..pythonFile)
end

-- Get window instance.
---@param windowInstanceMode? string
function getWindowInstance(windowInstanceMode)
    if UI.windowName == UI.undefined then
        error("Window not created.")

    else
        return io.open(UI.windowName..".py", windowInstanceMode)
    end
end

-- Delete window.
---@param windowName? string
function deleteWindow(windowName)
    if UI.windowName == UI.undefined then
        error("Window not created.")
    end

    local windowName = windowName:gsub("$currentWindow", UI.windowName)

    os.remove(windowName..".py") -- Removing window.
end

-- Exit from GUI.
---@param windowName? string
function killApp(windowName)
    addCode(windowName, 'kill()\n')
end

-- Exit from app.
function killLuaApp()
    os.exit()
end

-- Destroy code.
function destroy()
    error("Destroyed.", 3)
end

-- Memory check.
executePython("RAM.py") -- Getting RAM value.

-- Getting RAM.
MEMORY = io.open("RAM", "r")
PC_MEMORY = tonumber(MEMORY:read("*a"))
MEMORY:close()

if PC_MEMORY < MINIMAL_MEMORY then -- If RAM less than MINIMAL_MEMORY.
    error("Minimal RAM for library is 2GB. Your RAM: "..tostring(PC_MEMORY).."GB.", 0x3)
end
```

<h4>Go!</h4>
<br>

```
Ummmmmm.... I dont have it)
```

<h4>Java!</h4>
<b><a href="https://github.com/xzripper/JLanguageCreator/blob/main/LanguageCreator/StringParser.java">StringParser.java</a></b>
<br>
<br>

```java
package LanguageCreator;

public class StringParser {
    private String Str;

    /**
     * <h1>Tools for string parsing.</h1>
     * Create new instance of parser.
     * Now you using constructor.
     * @param Line The line.
     */
    public StringParser(String Line) {
        Str = Line;
    }

    /**
     * Cut string from start.
     * @param From Cut from.
     */
    public String CutStart(int From) {
        return Str.substring(From);
    }

    /**
     * Cut string from end.
     * @param From Cut from.
     */
    public String CutEnd(int From) {
        return Str.substring(0, Str.length() - From);
    }

    /**
     * Cut string from start and end.
     * @param Start Cut from start.
     * @param End Cut from end.
     */
    public String Cut(int Start, int End) {
        return Str.substring(Start, Str.length() - End);
    }


    /**
     * Strip the side.
     * If side will be invalid, function will return null.
     * <ul>
     *     <li>0 - Left.</li>
     *     <li>1 - Right.</li>
     *     <li>2 - Left and right.</li>
     * </ul>
     * @param Side Side to strip.
     */
    public String RemoveSpaces(int Side) {
        return switch (Side) {
            case 0 -> Str.stripLeading();
            case 1 -> Str.stripTrailing();
            case 2 -> Str.strip();
            default -> null;
        };
    }

    /**
     * Replace string.
     * If Old length is 1 and New length is 1, function just replaces old on new and returns new string.
     * If Old lenght not 1 and New length not 1, function replaces Old[Position] on New[Position]. If New will have more that Old or less that Old, returns null.
     * If error returns null.
     * @param Old String to replace.
     * @param New Replace on.
     */
    public String Replace(String[] Old, String[] New) {
        String Replaced = Str;

        if(Old.length == 1 && New.length == 1) {
            return Str.replace(Old[0], New[0]);
        } else if(Old.length > 1 && New.length > 1) {
            if(New.length > Old.length || New.length < Old.length) {
                return null;
            } else {
                for(int Index=0;Index<Old.length;Index++) {
                    Replaced = Replaced.replace(Old[Index], New[Index]);
                }

                return Replaced;
            }
        } else {
            return null;
        }
    }

    /**
     * Crash string by separator.
     * @param Separator The separator.
     */
    public String[] Crash(String Separator) {
        return Str.split(Separator);
    }

    /**
     * Split string by <i>separator</i><b>s</b>
     * Returns an array with splitted string step by step.
     * @param Separator The separator.
     */
    public String[][] Crash(String[] Separator) {
        String[][] Splitted = new String[Separator.length][Separator.length];

        for(int Index=0;Index<Separator.length;Index++) {
            Splitted[Index] = Str.split(Separator[Index]);
        }

        return Splitted;
    }

    /**
     * Remove substring from string.
     * @param Character
     */
    public String Remove(String Character) {
        return Str.replace(Character, "");
    }

    /**
     * Convert string to case.
     * If will be chosen unknown case, function will return null.
     * <ul>
     *     <li>Lower case - 1.</li>
     *     <li>Upper case - 2.</li>
     * </ul>
     * @param Case The case.
     */
    public String ToCase(int Case) {
        return switch (Case) {
            case 1 -> Str.toLowerCase();
            case 2 -> Str.toUpperCase();
            default -> null;
        };
    }

    /**
     * Get string from scobes.
     */
    public String GetFromScobes() {
        return Cut(1, 1);
    }

    /**
     * Is substring in string.
     * @param TheString The substring.
     */
    public boolean InString(String TheString) {
        return Str.contains(TheString);
    }

    /**
     * Convert array to string.
     * @param Array
     */
    public static String ArrayToString(String[] Array) {
        return String.format("<[%s]>", String.join(", ", Array));
    }

    /**
     * Update written string.
     */
    public void UpdateString(String Line) {
        Str = Line;
    }

    /**
     * Create new string.
     * @param Obj The string.
     */
    public String NewString(Object Obj) {
        return String.valueOf(Obj);
    }

    /**
     * Clean the string.
     */
    public void CleanString() {
        Str = null;
    }

    /**
     * Get written string.
     */
    public String GetString() {
        return Str;
    }
}
```

## End.
**Thank you for reading, have a good day, bye!**
<br>
<br>

<hr>
<p align="center">Bye!</p>
