build() called: 0 glasses
build() called: 1 glasses
build() called: 2 glasses
build() called: 3 glasses
build() called: 4 glasses
build() called: 5 glasses
build() called: 6 glasses

Activity2:
When I moved `_glasses++` outside `setState()` and tapped the + button,
the number of glasses did not update immediately on the screen.
The variable still increased, but Flutter was not notified to rebuild the UI.
Mao nang wala makita ang updated number. After the experiment, I put `_glasses++`
back inside `setState()` so the counter could update correctly whenever I tapped the button.

Activity 3: Removing Expanded from a StatBox:
When I removed Expanded from one StatBox,
I noticed that the boxes no longer shared the available width equally.
The box without Expanded could have a different width compared to the others,
making the layout less balanced. Mao ni akong na-learn nga useful ang Expanded para
equal ang spacing and mas organized ang weather dashboard, especially when using a Row.

Activity 5: Testing the Dark Mode and Save Button:
When I turned on the dark-mode switch, the app changed from light mode to dark mode.
The background, text, and other UI elements adjusted based on the selected theme.
When I turned the switch off, the app returned to light mode.
I also tapped the Save button, and a SnackBar appeared to show feedback that the settings were saved.
Through this activity, I learned that ThemeData controls the overall appearance of the app, while setState() updates the dark-mode value.
Nindot siya kay makita dayon ang changes without restarting the app.

### 1. What is the difference between a StatelessWidget and a StatefulWidget? Give one example of each from this lab.

A `StatelessWidget` is a widget nga dili mag-manage og changing state, like the `ProfileCard` in Activity 1, which displays my profile information. Meanwhile, a `StatefulWidget` can update its UI when its state changes. An example is the `WaterTrackerPage` in Activity 2, where the number of glasses changes when I tap the buttons.

### 2. Why is a StatefulWidget written as two classes? What does each class do?

A `StatefulWidget` has two classes because they have different responsibilities. The first class, `WaterTrackerPage`, defines the widget and creates its State object through `createState()`. The second class, `_WaterTrackerPageState`, holds the changing data, like `_glasses`, and contains the `build()` method and functions that update the UI. Basically, one defines the widget, while the other manages its changing state.

### 3. In Activity 2, what happened when you changed `_glasses` outside `setState()`? Why?

When I moved `_glasses++` outside `setState()`, the counter did not update immediately after tapping the plus button. This happened because Flutter was not notified that the state had changed. The variable could still change internally, but the UI would not rebuild because of that change. Mao nang important ang `setState()` para ma-update ang displayed value.

### 4. Looking at the Debug Console in Activity 2, when is `build()` called?

The `build()` method is called when the page is first displayed and whenever Flutter rebuilds the UI. In Activity 2, it runs again when I tap the plus or minus button or reset the tracker because these functions use `setState()`. The code uses `debugPrint()` to show the current number of glasses in the Debug Console. For example, the message could be `build() called: 1 glasses` after increasing the counter to one.

### 5. Explain the main axis and the cross axis of a Row and of a Column.

The main axis is the direction where the children are arranged, while the cross axis is perpendicular to it. In a `Row`, the main axis is horizontal and the cross axis is vertical. In a `Column`, the main axis is vertical and the cross axis is horizontal. These axes help control the alignment and spacing of widgets para mas organized ang UI.

### 6. In Activity 3, what happened when you removed `Expanded` from a `StatBox`? What does `Expanded` do?

When I removed `Expanded` from one `StatBox`, that box no longer shared the available width equally with the other boxes. It could take its natural width, making the boxes uneven and possibly causing overflow, especially on a smaller screen. The `Expanded` widget helps divide the remaining available space among the widgets. Mao ni siya makatabang para mas balanced ang layout.

### 7. Why do we use `GridView.builder` for the menu instead of a `Column` with many children?

We use `GridView.builder` because it displays the café menu in two columns, making the items more organized and easier to browse. It also builds items as needed instead of creating every item at once, which is useful for larger lists. Compared to a `Column`, it supports scrolling and a grid layout more conveniently.

### 8. How do `Stack` and `Positioned` create the Best seller badge in Activity 4?

The `Stack` widget allows multiple widgets to overlap, while `Positioned` places a widget at a specific location inside the stack. In Activity 4, the `Best seller` badge is placed near the top-left corner of a menu card using `Positioned(top: 8, left: 8)`. The badge only appears when the item's `bestSeller` value is `true`. Mao nang makita siya sa ibabaw sa card without changing the position of the main content.

### 9. What is the difference between customizing with `ThemeData` and with a style on one widget? Give one example of each from Activity 5.

`ThemeData` customizes the overall appearance of the app, so its colors and styles can apply to multiple widgets. In Activity 5, the `buildTheme()` function creates the light and dark themes used by `MaterialApp`. Meanwhile, styling one widget affects only that specific element. For example, the `My skills` text uses `Theme.of(context).textTheme.headlineSmall` to display it with a heading style. In short, `ThemeData` helps maintain a consistent design across the app, while a widget-specific style focuses on one element.

### 10. When you flip the dark-mode switch in Activity 5, which widget holds the state, and how does the change reach `MaterialApp`?

The `ThemeDemoApp` widget holds the dark-mode state in its State class through the `_isDark` Boolean variable. When I flip the switch, the `SettingsPage` calls the `onDarkChanged` callback provided by its parent. The parent updates `_isDark` inside `setState()`, then passes the updated value to `MaterialApp` through `themeMode`. Flutter rebuilds the app using the selected light or dark theme. Basically, the switch sends the change to the parent, and the parent updates the theme of the whole app.
