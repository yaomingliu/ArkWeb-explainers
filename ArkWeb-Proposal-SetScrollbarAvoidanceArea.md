# [Set Scrollbar avoidance area]

## Authors:

- [yaomingliu] ([ArkWeb])


## Participate
- [Issue tracker]
- [Discussion forum]

## Table of Contents [if the explainer is longer than one printed page]

[You can generate a Table of Contents for markdown documents using a tool like [doctoc](https://github.com/thlorenz/doctoc).]

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Introduction

The proposal adds a Scrollbar Avoidance Area CSS property, allowing web developers to dynamically set the scrollbar avoidance area and control the scrollbar to scroll only within a partial area of the viewport.

## User-Facing Problem

To provide users with an immersive experience, an app will display a webpage in full screen.


In this scenario, web content needs to avoid the status bar at the top and the bottom bar of the phone. Web developers can achieve this by obtaining the system's safe area from env() CSS function  and then setting padding for the web page.
env(safe-area-inset-top);
env(safe-area-inset-bottom);
However, the scrollbar cannot avoid the status bar and bottom bar through the same mechanism, as shown in the figure above, which brings an inconsistent experience to users.

For devices with non-rectangular screen, Webpages usually need set avoidance area to ensure the web contents and scrollbar are visible to users.


### Goals [or Motivating Use Cases, or Scenarios]
Allowing web developers to dynamically set the scrollbar avoidance area and control the scrollbar to scroll only within a partial area of the viewport.


## Proposed Approach
We propose adding the CSS properties scrollbar-avoidance-area-top, scrollbar-avoidance-area-bottom, scrollbar-avoidance-area-left, and scrollbar-avoidance-area-right, allowing developers to dynamically set the scrollbar avoidance areas and control the scrollbar to scroll only within a partial area of the viewport. 


### Solving dynamically set the scrollbar avoidance area with this approach
```
// Use cases to illustrate the idea. As much as possible
<!--index.html-->
<!DOCTYPE html>
<html>
	<head>
  	<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
		<title>Demo</title>
		<style>
			body {
				width:2560px;
				height:2560px;

				padding-top: env(safe-area-inset-top);
				padding-bottom: env(safe-area-inset-bottom);
				padding-left: env(safe-area-inset-left);
				padding-right: env(safe-area-inset-right);

				scrollbar-avoidance-area-top:env(safe-area-inset-top);
				scrollbar-avoidance-area-bottom:env(safe-area-inset-bottom);
				scrollbar-avoidance-area-left:env(safe-area-inset-left);
				scrollbar-avoidance-area-right:env(safe-area-inset-right);

				border:5px solid blueviolet
			}
		</style>
	</head>
	<body>
		set avoidance area for web content and scrollbar Test
	</body>
</html>
```

## Accessibility, Privacy, and Security Considerations

NA

## References & acknowledgements

Many thanks for valuable feedback and advice from:

- [Person 1]
- [etc.]

Thanks to the following proposals, projects, libraries, frameworks, and languages
for their work on similar problems that influenced this proposal.

- [ArkWeb]
