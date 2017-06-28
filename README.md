StrInsert (String Insert)
=========================

Button for the CKEditor to insert custom defined values into the editor. Sounds pretty bland but enables a much nicer editing experience for end-users in e.g. DokuWiki.

## Usage & Why the forking?
* The last commit to the original repository is 2 years old
* I used this plugin in DokuWiki together with the ckgdoku plugin, which is basically the same as the ckeditor
* When I tried to store some plugin syntax as values I stumbled on this issue with HTML-Entities: https://dev.ckeditor.com/ticket/11701
* I found a quick fix and will push it into this repository
* I used ckgdoku & this plugin with my modifications to create a "macro"-button for the toolbar to help users who don't want or simply don't have the time to learn the DokuWiki syntax (+ the syntax for all the plugins that may be useful)
* I myself forget the syntax of plugins I just use once in a while, so it is not only nice for users who are not familiar to the (Doku)Wiki syntax


## Heritage
Original repository name custom-dropdown-ckeditor4.

By Stuart Sillitoe (57u) and Marcus Bointon (Synchro).

 * https://github.com/57u/custom-dropdown-ckeditor4
 * https://github.com/Synchro/custom-dropdown-ckeditor4

## Installation

1. Create a folder named `strinsert` in the `/lib/plugins/ckgdoku/ckeditor/plugins/` directory
2. Copy the `plugin.js` into the folder
3. Go to your global DokuWiki settings and into the ckgdoku section
4. In `plugin»ckgdoku»extra_plugins` add `strinsert` to the comma separated list and save
5. When you edit a page with ckgdoku, a new button with the label `insert` should appear

## Configuration

Add the values you are going to insert to your configuration in the `plugin.js`, like this:

```
CKEDITOR.editorConfig = function( config ) {

    // ...
    config.strinsert_strings = [
			{'name': 'Name', 'value': '*|VALUE|*'},
			{'name': 'Group 1'},
			{'name': 'Another name', 'value': 'totally_different', 'label': 'Good looking'},
		];
};
```

This list of dicts define the strings to choose from to insert into the editor.

Each insertable string dict is defined by three possible keys:
 * 'value': The value to insert.
 * 'name': The name for the string to use in the dropdown.
 * 'label': The voice label (also used as the tooltip title) for the string.

Only the value to insert is required to define an insertable string, the value will be used as the name (and the name as the label) if other keys are not provided.

If the value key is *not* defined and the name key is, then a group header with the given name will be provided in the dropdown box.  This heading is not clickable and does not insert, it is for organizational purposes only.

### Additional configuration

You can additionally set name shown for the dropdown button with **config.strinsert_button_label** ('Insert' by default) and the title/tooltip text with  **config.strinsert_button_title** and the voice label text **config.strinsert_button_voice** (both 'Insert content' by default).

## Available DokuWiki Macros
I have added these macros (*syntax snippets for using some DokuWiki plugins and native syntax*) so far:

### Zitat
```> Zitat eingeben…```

### Autoren
```~~AUTHORS~~```

### Seiten
```<nspages -simpleList>```

### No Cache
```~~NOCACHE~~```

### No TOC
```~~NOTOC~~```

### ACL Info
```~~ACLINFO~~```

### Image gallery
```{{gallery>?crop&lightbox}}```

### Comment
```/* Insert comment here */```


## TODO
* ~~add HTML-Entity fix~~
* ~~add basic DokuWiki macros entries~~
* ~~add macro info to documentation~~
* add macro links to documentation
