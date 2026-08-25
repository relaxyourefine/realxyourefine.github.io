# lionguide.org

The Lion Guide website. It is one page, and that page is the file
**`index.html`**. Everything you see on the site — the words, the layout,
the colours — lives in that single file.

You do not need to install anything, run anything, or "build" anything.
Edit the file, save it, and it goes live.

---

## The files

| File | What it does |
| --- | --- |
| `index.html` | **The whole website.** This is the only file you will normally edit. |
| `CNAME` | Tells GitHub the site lives at `lionguide.org`. Don't touch this. |
| `.nojekyll` | Tells GitHub not to process the site. Don't touch this. |
| `README.md` | This file. Notes for you, not shown on the website. |
| `.gitignore` | Tells Git to ignore junk files. Don't touch this. |

## Finding your way around `index.html`

The spots you are most likely to change are marked with a comment that says
`EDIT ME`. Use your editor's Find (**Ctrl+F**, or **Cmd+F** on a Mac) and
search for `EDIT ME` to jump between them.

Comments look like `<!-- like this -->`. They are notes to yourself — the
website never displays them.

---

## How to edit the tour info

The tour details are the list under the heading "Booked ahead, kept small."
Search for `Booked ahead` to find it. Each line looks like this:

```html
<li class="row">
  <span class="row__k">Group size</span>
  <span class="row__v">Six people maximum. Most tours are a single family.</span>
</li>
```

- `row__k` is the label on the left ("Group size").
- `row__v` is the description on the right.

Change the words between `>` and `<`. Leave the tags themselves alone.

To **remove** a row, delete the whole block from `<li class="row">` down to
`</li>`. To **add** one, copy an existing block and change the words.

To change the headline at the top of the page, search for
`Columbia, walked properly.` and edit it there.

## How to change your phone number

Your number appears in **four** places, each marked `<!-- EDIT ME - PHONE -->`.
Change all four or the site will be inconsistent.

Each one looks like this:

```html
<a href="tel:+15551234567">(555) 123-4567</a>
```

There are two different formats in that line, and both need updating:

- `tel:+15551234567` — this is what the phone actually dials. Write it with
  a `+`, then `1` for the US, then your ten digits, **no spaces, brackets or
  dashes**.
- `(555) 123-4567` — this is what visitors read on screen. Format it however
  looks nice.

So for the number 212 555 0147 you would write:

```html
<a href="tel:+12125550147">(212) 555-0147</a>
```

## How to update the contact form

The form emails you whenever someone fills it in. It runs on a free service
called **Web3Forms**, which needs one setup step: an access key.

**Getting your key (one time only):**

1. Go to **https://web3forms.com**
2. Enter the email address where you want enquiries to arrive.
3. Web3Forms emails you an access key — a long string that looks a bit like
   `a1b2c3d4-e5f6-7890-abcd-ef1234567890`.
4. Open `index.html` and search for `YOUR_ACCESS_KEY_HERE`.
5. Replace **just** that text with your key, keeping the quote marks:

   ```html
   <input type="hidden" name="access_key" value="a1b2c3d4-e5f6-7890-abcd-ef1234567890">
   ```

6. Save, and publish the change (see "How a change goes live" below).
7. Send yourself a test enquiry through the live site to confirm it arrives.
   Check your spam folder the first time.

It is safe for this key to be visible in the code. That is how Web3Forms is
designed to work — the key only lets people send you messages.

**Changing the questions:** each question is a block marked `class="field"`.
Copy one to add a question, delete one to remove it. Whatever the visitor
types is emailed to you under the name in `name="..."`, so give each field a
different name.

**Changing where the email goes:** get a new access key using the new email
address, and paste it in place of the old one.

## How to add a new page

Say you want a page about pricing.

1. Make a copy of `index.html` and name it `pricing.html`. Use lowercase
   letters and no spaces — use a dash instead, like `about-me.html`.
2. Open `pricing.html` and delete the sections you don't want, then write
   your content.
3. Link to it from `index.html` by adding a link somewhere sensible:

   ```html
   <a href="/pricing.html">Pricing</a>
   ```

4. Publish the change. The page will be live at `lionguide.org/pricing.html`.

`index.html` is special: it is what people see at `lionguide.org` itself.
Don't rename it.

## How to change the photos

All the photos live in the **`pictures`** folder. There are four:

| File | Where it appears |
| --- | --- |
| `grad.jpg` | The big photo at the top, beside the headline |
| `boat.jpg` | Bottom row, left |
| `met.jpg` | Bottom row, middle |
| `winter.jpg` | Bottom row, right |

**To swap one out,** put your new picture in the `pictures` folder and
change the matching `src="pictures/..."` in `index.html`. The spots are
marked `EDIT ME - PHOTO` and `EDIT ME - GALLERY`.

Three things to keep right:

1. **Resize first.** A photo straight off a phone can be 6MB and will make
   the page slow. Aim for about 900 pixels wide for the top photo and 700
   for the bottom three. Any free online image resizer will do this.
2. **Update `width` and `height`** on that `<img>` to match your new file's
   real dimensions. If these are wrong the page jumps around while loading.
3. **Write the `alt` text.** That is the description read aloud to blind
   visitors and shown if the image fails to load. Describe what is in the
   photo in a short sentence.

**If a photo looks badly cropped:** the bottom three are tall pictures shown
in square frames, so the top and bottom get trimmed. Add or adjust
`style="object-position:center 32%"` on that `<img>` — a smaller percentage
keeps more of the top of the picture, a larger one keeps more of the bottom.
`winter.jpg` already uses this.

## How a change goes live

The site is hosted by GitHub Pages. Anything saved to the **`main`** branch
is published automatically to lionguide.org.

**The easy way, in your browser:**

1. Go to https://github.com/relaxyourefine/relaxyourefine.github.io
2. Click the file you want to change (`index.html`).
3. Click the pencil icon at the top right.
4. Make your edit.
5. Click **Commit changes**, write a short note about what you changed
   (like "updated phone number"), and confirm.

That's it. Give it **one to two minutes**, then reload lionguide.org. If you
don't see the change, do a hard refresh — **Ctrl+Shift+R**, or
**Cmd+Shift+R** on a Mac — as your browser may be showing you a saved copy.

You can watch it publish under the **Actions** tab on GitHub. A green tick
means it's live; a red X means something went wrong.

**If you edit files on your computer instead,** you need to send them to
GitHub afterwards:

```bash
git add -A
git commit -m "short note about what changed"
git push
```

## If something breaks

Nothing you do here is permanent — GitHub keeps every previous version.

To undo a change, open the repository on GitHub, click **Commits**, find the
version from before things broke, and copy the file contents back.

The most common cause of a broken page is a deleted or mismatched tag. Every
`<div>` needs a matching `</div>`. If the page looks scrambled, you probably
deleted one half of a pair.
